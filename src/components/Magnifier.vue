<template>
  <div class="glass" v-show="active && shown" :style="glassStyle">
    <div ref="lens" class="lens"></div>

    <!-- рамка лупы с ручкой -->
    <svg class="frame" :width="size" :height="size" viewBox="0 0 100 100" aria-hidden="true">
      <circle cx="50" cy="50" r="47" fill="transparent" stroke="rgba(0,0,0,.85)" stroke-width="6"/>
      <circle cx="50" cy="50" r="44" fill="transparent" stroke="white" stroke-opacity=".9" stroke-width="2"/>
      <path d="M22 40 C35 20, 65 20, 78 40" fill="transparent" stroke="rgba(255,255,255,.35)" stroke-width="4" stroke-linecap="round"/>
      <g transform="translate(50,50) rotate(35)">
        <rect x="40" y="-6" width="36" height="12" rx="6" fill="rgba(0,0,0,.85)"/>
        <rect x="40" y="-4" width="36" height="8" rx="4" fill="rgba(255,255,255,.25)"/>
      </g>
    </svg>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const props = defineProps({
  target: { type: Object, required: true }, // ref<HTMLImageElement>
  zoom:   { type: Number, default: 2.0 },
  size:   { type: Number, default: 160 },
  active: { type: Boolean, default: false }
})

const lens = ref(null)
const shown = ref(false)
const glassStyle = ref({ left: '0px', top: '0px' })

let imgEl
let onEnter, onLeave, onMove
const r = props.size / 2
const clamp = (v, a, b) => Math.max(a, Math.min(b, v))

function setupLens(){
  imgEl = props.target?.value
  const l = lens.value
  if(!imgEl || !l) return
  l.style.width = l.style.height = props.size + 'px'
  l.style.borderRadius = '50%'
  l.style.backgroundImage = `url('${imgEl.src}')`
  l.style.backgroundSize = `${imgEl.clientWidth * props.zoom}px ${imgEl.clientHeight * props.zoom}px`
}

onMounted(() => {
  setupLens()
  const img = props.target?.value
  if(!img) return

  onEnter = () => { if(props.active){ setupLens(); shown.value = true } }
  onLeave = () => { shown.value = false }
  onMove  = (e) => {
    if(!props.active) return
    const rect = img.getBoundingClientRect()
    const x = e.clientX - rect.left
    const y = e.clientY - rect.top
    const cx = clamp(x, r, img.clientWidth  - r)
    const cy = clamp(y, r, img.clientHeight - r)
    glassStyle.value = { left: (rect.left + cx - r) + 'px', top: (rect.top + cy - r) + 'px' }
    lens.value.style.backgroundPosition = `-${(cx * props.zoom) - r}px -${(cy * props.zoom) - r}px`
  }

  img.addEventListener('mouseenter', onEnter)
  img.addEventListener('mouseleave', onLeave)
  img.addEventListener('mousemove',  onMove)
})

onBeforeUnmount(() => {
  const img = props.target?.value
  if(!img) return
  img.removeEventListener('mouseenter', onEnter)
  img.removeEventListener('mouseleave', onLeave)
  img.removeEventListener('mousemove',  onMove)
})
</script>

<style lang="sass" scoped>
.glass
  position: fixed
  pointer-events: none
  z-index: 1000

.lens
  position: absolute
  left: 0
  top: 0
  background-repeat: no-repeat
  box-shadow: inset 0 0 0 2px rgba(255,255,255,.35), 0 10px 22px rgba(0,0,0,.25)

.frame
  position: absolute
  left: 0
  top: 0
  width: 100%
  height: 100%
</style>