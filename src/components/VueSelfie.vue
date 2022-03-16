<template>
  <div>
    <h2>VUE SELFIE APP</h2>
    <video ref="video" @canplay="initCanvas()">Stream available</video>
    <button @click="takePicture()">Take picture</button>
    <canvas ref="canvas" style="display: none;" />
  </div>
</template>
<script>
export default {
  name: "VueSelfie",
  mounted(){
      this.canvas = this.$refs.canvas
      this.video = this.$refs.video
      this.startCapture()
  },
  methods:{
      startCapture(){
          navigator.mediaDevices.getUserMedia({video: true, audio: false}).then(stream => {
              this.video.srcObject = stream
              this.video.play()
          }).catch(error =>{
              console.log(error)
          })
      },
      takePicture(){
          let context = this.canvas.getContext('2d')
          context.drawImage(this.video, 0, 0, this.video.videoWidth, this.video.videoHeight)
          this.$emit('picture-taken', this.canvas.toDataURL('image/png'))
      },
      initCanvas(){
          this.canvas.setAttribute('width', this.video.videoWidth)
          this.canvas.setAttribute('height', this.video.videoHeight)
      }
  },
  data(){
      return{
          video : null,
          canvas: null
      }
  }
}
</script>
