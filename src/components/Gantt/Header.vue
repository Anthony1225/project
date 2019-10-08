<template>
    <div class="ganttButtonBar noprint">
    <div class="buttons">
      <button class="button textual icon requireCanWrite" title="undo"><span class="teamworkIcon">&#39;</span></button>
      <button class="button textual icon requireCanWrite" title="redo"><span class="teamworkIcon">&middot;</span></button>
      <span class="ganttButtonSeparator requireCanWrite requireCanAdd"></span>
      <button class="button textual icon requireCanWrite requireCanAdd" title="insert above"><span class="teamworkIcon">l</span></button>
      <button class="button textual icon requireCanWrite requireCanAdd" title="insert below"><span class="teamworkIcon">X</span></button>
      <span class="ganttButtonSeparator requireCanWrite requireCanInOutdent"></span>
      <button class="button textual icon requireCanWrite requireCanInOutdent" title="un-indent task"><span class="teamworkIcon">.</span></button>
      <button class="button textual icon requireCanWrite requireCanInOutdent" title="indent task"><span class="teamworkIcon">:</span></button>
      <span class="ganttButtonSeparator requireCanWrite requireCanMoveUpDown"></span>
      <button  class="button textual icon requireCanWrite requireCanMoveUpDown" title="move up"><span class="teamworkIcon">k</span></button>
      <button  class="button textual icon requireCanWrite requireCanMoveUpDown" title="move down"><span class="teamworkIcon">j</span></button>
      <span class="ganttButtonSeparator requireCanWrite requireCanDelete"></span>
      <button  class="button textual icon delete requireCanWrite" title="Elimina"><span class="teamworkIcon">&cent;</span></button>
      <span class="ganttButtonSeparator"></span>
      <button  class="button textual icon " title="EXPAND_ALL"><span class="teamworkIcon">6</span></button>
      <button  class="button textual icon " title="COLLAPSE_ALL"><span class="teamworkIcon">5</span></button>

    <span class="ganttButtonSeparator"></span>
      <button class="button textual icon " title="zoom out"><span class="teamworkIcon">)</span></button>
      <button class="button textual icon " title="zoom in"><span class="teamworkIcon">(</span></button>
    <span class="ganttButtonSeparator"></span>
      <button class="button textual icon " title="Print"><span class="teamworkIcon">p</span></button>
    <span class="ganttButtonSeparator"></span>
      <button class="button textual icon requireCanSeeCriticalPath" title="CRITICAL_PATH"><span class="teamworkIcon">&pound;</span></button>
    <span class="ganttButtonSeparator requireCanSeeCriticalPath"></span>
      <button class="button textual icon" ><span class="teamworkIcon">F</span></button>
      <button class="button textual icon" ><span class="teamworkIcon">O</span></button>
      <button  class="button textual icon"><span class="teamworkIcon">R</span></button>
      <span class="ganttButtonSeparator"></span>
      <button class="button textual icon" title="FULLSCREEN" id="fullscrbtn"><span class="teamworkIcon">@</span></button>
      <button  class="button textual icon"><span class="teamworkIcon">&sect;</span></button>

    <button class="button textual requireWrite" title="edit resources"><span class="teamworkIcon">M</span></button>
      &nbsp; &nbsp; &nbsp; &nbsp;
    <button class="button first big requireWrite" title="Save">Save</button>
    <button  class='button requireWrite newproject'><em>clear project</em></button>
    <button class="button login" title="login/enroll"  style="display:none;">login/enroll</button>
    <button class="button opt collab" title="Start with Twproject" style="display:none;"><em>collaborate</em></button>
    </div></div>

</template>
<script>
export default {
    
}
</script>
<style lang="scss" scoped>
@font-face {
  font-family: 'TeamworkRegular';
  src: url('../../res/icons.eot?5qjga5');
  src: url('../../res/icons.eot?#iefix5qjga5') format('embedded-opentype'),
  url('../../res/icons.woff?5qjga5') format('woff'),
  url('../../res/icons.ttf?5qjga5') format('truetype'),
  url('../../res/icons.svg?5qjga5#icons') format('svg');
  // font-weight: normal !important;
  // font-style: normal;
}


.ganttButtonBar{
  position:relative;
  z-index: 2;
  /*background-color: #fff;*/
  border-bottom: 1px solid #959595;
  padding: 5px 0 5px 10px;
}

.dataTable .ganttButtonBar{
  border-bottom: none;
}

.ganttButtonBar .buttons {
  position: relative;
  display:inline-block;
  width: 100%;
  margin-top: 0;
  height: 45px;
}

.dataTable .ganttButtonBar .buttons {
  display:inline-block;
  width: 100%;
}

.ganttButtonBar .buttons button{
  vertical-align: middle;
  margin:0;
  outline: none;
}

.ganttButtonBar .buttons .button.textual.icon {
  height: 45px;
}

.button span.teamworkIcon {
  text-indent: -10px;
}

.ganttButtonSeparator{
  border-left:1px solid #dadada;
  margin:0 10px;
  font-size: 130%;
  vertical-align: middle;
}

.ganttButtonBar .buttons button{
  vertical-align: middle;
  margin:0;
  outline: none;
}

.button {
  display: inline-block;
  font-size: 110%;
  color: #fff;
  cursor: pointer;
  background-color: #34495e;
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  -o-border-radius: 5px;
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.2);
  padding: 5px 12px 8px;
  margin-bottom: 10px;
  margin-right: 10px;
  text-align: center;
  -webkit-transition: background-color 500ms ease-out 1s;
  -moz-transition: background-color 500ms ease-out 1s;
  -o-transition: background-color 500ms ease-out 1s;
  transition: background-color 500ms ease-out 1s;
}

.button.first {
  background-color: #75a800;
  font-weight: bold;
}

.button.textual, .button.buttonImg {
  border: none;
  background-color: transparent;
  color: #68979B;
  -moz-border-radius: 0;
  -webkit-border-radius: 0;
  -o-border-radius: 0;
  border-radius: 0;
  padding: 0;
  margin: 0;
  text-align: left
}
/*
-------------------------------------------------------
teamwork icon
-------------------------------------------------------
*/

.teamworkIcon {
  font-family: 'TeamworkRegular' !important;
  color: #34495e;
  font-weight: normal;
  font-size: 120%;
  font-style: normal !important;
  text-rendering: optimizelegibility;
  -webkit-font-smoothing: antialiased;
  -moz-font-smoothing: antialiased;

}

.teamworkIcon:hover {
  opacity: .8
}

.teamworkIcon.withLabel {
  padding-right: 5px;
}

.button:hover .teamworkIcon {
  opacity: 0.8
}

.teamworkIcon.alert {
  color: #B61E2D;
}
/*--------------------------------------------------- Media queries  --------------------------------------------------*/

/* Large screens */

// @media only screen and (max-width : 1260px) {

//   .ganttButtonBar .button span.teamworkIcon {
//     font-size: 130%;
//   }
//   .userLine {
//     display: none;
//   }

// }

// @media only screen and (min-width : 1261px) and (max-width : 1320px) {

//   .ganttButtonBar .button span.teamworkIcon {
//     font-size: 130%;
//   }

//   .button {
//     font-size: 100%;
//     padding: 3px 9px 6px;
//     margin-right: 5px;
//     margin-bottom: 5px
//   }

//   .userLine {
//     display: none;
//   }

// }

// @media only screen and (max-width : 1160px) {

//   .userProfile {
//     float: none;
//     position: absolute;
//     top:0;
//     right: 10px;
//   }

//   .userProfile .teamworkIcon {
//     color: rgb(255, 255, 255);
//   }
//   .userProfile .ganttButtonSeparator, .userProfile .avatar {
//     border-color: rgb(127, 154, 170);
//   }

// }

// /* Ipad */

// @media only screen and  (min-width: 768px) and (max-width: 1024px){
//   .ganttButtonSeparator {
//     margin-left: 2px;
//     padding-right: 6px;
//     font-size: 100%;
//   }
//   .button {
//     padding: 5px 6px 6px;
//   }
// }

// /* Mobile TODO */

// @media only screen and (max-width: 767px) {
//   .button {
//     font-size: 50%;
//   }
// }

</style>
