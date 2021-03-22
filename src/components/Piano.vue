<template>
  <v-stage :config="configKonva">
      <v-layer>
          <v-rect
            v-for="(tecla, index) in naturalNote" :key="index"
            @click="generarAudio(tecla.name)"
            :config="{
                x: positionKey(tecla.type, index),
                y: 100,
                height: 100,
                width: 25,
                fill: '#fff',
                stroke: '#000',
              }">
            </v-rect>
      </v-layer>
      <v-layer>
        <v-rect
          v-for="(tecla, index) in sharpNote" :key="index"
          @click="generarAudio(tecla.name)"
          :config="{
              x: positionKey(tecla.type, index),
              y: 100,
              height: 50,
              width: 25/2,
              fill: '#000',
            }">
          </v-rect>
      </v-layer>
  </v-stage>
</template>

<script>

export default {
  name: 'Piano',
  data() {
    return {
      teclas: [
        {name: 'C', type: 'natural'},
        {name: 'Csharp', type: 'S/F'},
        {name: 'D', type: 'natural'},
        {name: 'Dsharp', type: 'S/F'},
        {name: 'E', type: 'natural'},
        {name: 'F', type: 'natural'},
        {name: 'Fsharp', type: 'S/F'},
        {name: 'G', type: 'natural'},
        {name: 'Gsharp', type: 'S/F'},
        {name: 'A', type: 'natural'},
        {name: 'Asharp', type: 'S/F'},
        {name: 'B', type: 'natural'},
        {name: 'C2', type: 'natural'}
      ],
      configKonva: {
        width: window.innerWidth,
        height: window.innerHeight/2,
      }
    };
  },
  computed:{
    naturalNote(){
      return this.teclas.filter(note => note.type == 'natural')
    },
    sharpNote(){
      return this.teclas.filter(note => note.type == 'S/F')
    },
  },
  methods:{
    positionKey(type, index){
      let position = 0;

      if(type == 'natural'){
        position = (index+1)*25;
      }else{
        let arrayPosition = [43.73, 68.75, 118.75, 143.75, 168.75]
        position = arrayPosition[index]
      }

      return position;
    },
    generarAudio(noteName){
      const audio = new Audio();
      audio.src = 'assets/audios/' + noteName + '.mp3';
      audio.load();
      audio.play();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
