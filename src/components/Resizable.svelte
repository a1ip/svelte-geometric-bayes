<script>
  export let width = 50,
    height = 50
  export let pos = `top: 0; left: 0;`
  export let handlePos = `top: 0; left: 0;`
  export let parentWidth, parentHeight

  export let color
  export let resizable = `xy` // `x`, `y` or `xy`

  let resizeInitX, resizeInitY

  let initialWidth, initialHeight

  const resizePointerDown = (e) => {
    e.stopPropagation()
    resizeInitX = e.pageX
    resizeInitY = e.pageY

    initialWidth = width
    initialHeight = height

    window.addEventListener(`pointermove`, resizePointerMove)
    window.addEventListener(`pointerup`, resizePointerUp)
    window.addEventListener(`pointercancel`, resizePointerUp)
  }

  const resizePointerMove = (e) => {
    let dirX = pos.includes(`right`) ? -1 : 1
    let dirY = pos.includes(`bottom`) ? -1 : 1
    let scaleX = parentWidth / 100
    let scaleY = parentHeight / 100
    if (resizable.includes(`x`)) {
      let newWidth = (initialWidth * dirX + (e.pageX - resizeInitX) / scaleX) * dirX
      width = Math.min(100, Math.max(0, newWidth)) // prevent extending beyond container
    }
    if (resizable.includes(`y`)) {
      let newHeight = (initialHeight * dirY + (e.pageY - resizeInitY) / scaleY) * dirY
      height = Math.min(100, Math.max(0, newHeight)) // prevent extending beyond container
    }
  }

  const resizePointerUp = () => {
    window.removeEventListener(`pointermove`, resizePointerMove)
    window.removeEventListener(`pointerup`, resizePointerUp)
    window.removeEventListener(`pointercancel`, resizePointerUp)
  }
</script>

<div
  class="resizable"
  style="{pos} width: {width}%; height:{height}%; background: {color};"
>
  <slot />
  <div class="resizer" on:pointerdown={resizePointerDown} style={handlePos} />
</div>

<style>
  .resizable {
    touch-action: none;
    position: absolute;
    will-change: transform;
    /* use box-shadow instead of border to achieve border collapse: https://stackoverflow.com/a/28807765 */
    box-shadow: 2px 0 0 0 white, 0 2px 0 0 white, 2px 0 0 0 white inset,
      0 2px 0 0 white inset;
  }
  .resizer {
    user-select: none;
    position: absolute;
    right: 0;
    bottom: 0;
    cursor: pointer; /* consider using 'nw-resize' and friends */
    width: calc(1ex + 2vw);
    max-width: 2ex;
    height: calc(1ex + 2vw);
    max-height: 2ex;
    background: orange;
    border: 2px solid white;
    border-radius: 50%;
    transform: translate(-50%, -50%);
  }
</style>
