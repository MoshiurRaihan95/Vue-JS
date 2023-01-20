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

    <!-- 
    ******* Conditional Rendering 
    v-if
    v-else
    v-else-if
    v-show
    -->
    <h2 v-if="num === 0">The number is zero</h2>
    <h2 v-else-if="num < 0">The number is negative</h2>
    <h2 v-else-if="num > 0">The number is positive</h2>
    <h2 v-else>Not a number</h2>

    <div v-bind:style="dispalyStyle" v-if="display">
      <h2>Hello</h2>
      <h2>Vue</h2>
      <h2>Js</h2>
      <h2 v-show="showElement">Using v-show</h2> 
      <h2 v-if="showElement">Using v-if</h2> 
    </div>

    <!-- 
      ********List rendering*********
      ####V-for Directive####

      Array Of String
      Array of Objects
      Array of Arrays
      Block of HTML elements
      Object Key Value Pairs
    -->
    <div v-bind:style="listRendering">
      <h1>List Rendering</h1>
      <h2 v-for="(name, index) in names" :key="name">{{index}} {{name}}</h2>
      <h2 v-for="name in fulNames" :key="name.first">{{name.firstName}} {{name.lastName}}</h2>
      <div v-for="actor in actors" :key="actor.name" v-bind:style="movieList">
        <h2>{{actor.name}}</h2>
        <h3 v-for="movie in actor.movies" :key="movie">{{movie}}</h3>
      </div>
      <div v-bind:style="myInfoStyle">
        <h2 v-for="(value, key, index) in myInfo" :key="value">{{index}}. {{key}}: {{value}}</h2>
      </div>
    </div>

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
      },

      /**
      ******* Conditional Rendering 
      v-if
      v-else
      v-else-if
      v-show
      */
      num: "Raihan",
      display: true,
      showElement: true,
      dispalyStyle:{
        backgroundColor: 'lightgreen',
        border: '1px solid lightgreen',
        borderRadius: '5px',
        color: 'white',
        fontSize: '20px'
      },

      /* 
      ********List rendering*********
      ####V-for Directive####

      Array Of String
      Array of Objects
      Array of Arrays
      Block of HTML elements
      Object Key Value Pairs
      */
      names: ['Ibrahim the....', 'Khairul the...', 'Anisur..'],
      fulNames: [
        {firstName: 'Ibrahim', lastName: 'Kholil'},
        {firstName: 'Khairul', lastName: 'Islam'},
        {firstName: 'Anisur', lastName: 'Rahman'},
      ],
      actors: [
        {
          name: 'Chistain Bale',
          movies: ['Batman', 'The Pestige'],
        },
        {
          name: 'Di Caprio',
          movies: ['Titanic', 'Inception'],
        },
      ],
      myInfo: {
        name: 'Vishwas',
        channel: 'Codevolution',
        course: 'Vue 3'
      },
      listRendering:{
        backgroundColor: 'salmon',
        padding: '15px',
        borderRadius: '5px',
        color: 'white',
        marginTop: '20px',
      },
      movieList:{
        backgroundColor: 'lightSalmon',
        padding: '15px',
        borderRadius: '5px',
        color: 'Gainsboro',
      },
      myInfoStyle:{
        backgroundColor: 'DarkSlateGray',
        borderRadius: '5px',
        padding: '10px',
        marginTop: '15px',
      },
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
