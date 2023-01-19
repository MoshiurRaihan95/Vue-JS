<template>
  <div>
    <h3>{{greet}} {{ name }}</h3>
    <div v-html="channel"></div>
    <div v-html="hack"></div>
    <h2 v-bind:id="headingId">Heading</h2>
    <button v-bind:disabled="isDisabled">Bind</button>
    <h2 class="underline">Underline Text</h2>
    <h2 class="underline" v-bind:class="status">Status</h2>
    <h3 v-bind:class="isPromoted && 'promoted'">Promoted Movie</h3>
    <h2 v-bind:class="isSoldout ? 'sold_out' : 'new'">Soldout Movie</h2>
    <h2 v-bind:class="['new','promoted']">Newly Promoted Movie</h2>
    <h2 v-bind:class="[isPromoted && 'promoted', isSoldout ? 'sold_out' : 'new']">Array Conditional Movie</h2>
    <h2 v-bind:class="{
      promoted: isPromoted,
      new: !isSoldout,
      'sold-out': isSoldout,
    }">Object Conditional Movie</h2>
    <h2 v-bind:style="{
      color: highLightColor,
      'font-size': headerSize + 'px',
    }">Inline Style</h2>

    <h2 v-bind:style="headerStyleObject">Style Object</h2>

    <div v-bind:style="[baseStyleObject, successStyleObject]">Success Style</div>
    
    <div v-bind:style="[baseStyleObject, dangerStyleObject]">Danger Style</div>

  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      greet: "Hello",
      name: "Raihan",
      channel: '<b>Learn Vue</b>',
      hack: `<a href="3" onclick="alert('You have been hacked')">Win a Prize!</a>`,
      headingId: 'heading',
      isDisabled: false,
      status: 'danger',
      isPromoted: true,
      isSoldout: false,
      highLightColor: 'orange',
      headerSize: 50,
      headerStyleObject:{
        color: 'orange',
        fontSize: '60px',
        padding: '20px',
        textTransform: 'uppercase',
        fontWeight: '900'
      },
      baseStyleObject:{
        fontSize: '40px',
        padding: '15px',
        fontWeight: '600'
      },
      successStyleObject:{
        color: 'grren',
        backgroundColor: 'lightgreen',
        border: '1px solid green',
        borderRadius: '5px'
      },
      dangerStyleObject:{
        color: 'darkred',
        backgroundColor: 'red',
        border: '1px solid darkred',
        borderRadius: '5px',
        marginTop: '20px'
      }
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.underline{
  text-decoration: underline;
}
.promoted{
  font-style: italic;
}
.new{
  color: olivedrab;
}
.sold_out{
  color: red;
}
</style>
