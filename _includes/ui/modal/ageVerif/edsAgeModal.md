<style type="text/css">
.svgFlagCntr{
  height: 100%;
  width:  140px;
}
.svgFlagCntr.LHS{margin-right: 1px;}
.svgFlagCntr.RHS{margin-left:  1px;}

.svgFlags path{
  fill: black;
}
.svgFlags text{
  fill: #cecece;
  font-size: 25px;
}
.svgFlags text:hover{
  fill: #FFFFFF;
}
.svgFlags path:hover ~ text{
  fill: #FFFFFF;
}
.modal-content {
    background-color: #DAB677; //var(--bs-modal-bg);
    border-top-right-radius: 1rem;
    border-top-left-radius:  1rem;
    border-bottom-right-radius: 0px;
    border-bottom-left-radius: 0px;
    cursor: default; /*bfd*/
}
.modal-header {
    border-bottom: 0px;
}
.modal-body {
    padding: var(--bs-modal-padding) 2px
}
.modal-footer {
    border-bottom-right-radius: 0px;
    border-bottom-left-radius: 0px;
    border-top: 0px;
}
.modal-dialog {
    position:absolute;
    bottom:0;
    right:3vw;
    margin: 0px;
    border-bottom-right-radius: 0px;
    border-bottom-left-radius: 0px;
}
</style>

<div class="modal fade" id="staticBackdrop" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1" aria-labelledby="staticBackdropLabel" aria-hidden="true">
  <div class="modal-dialog modal-lg">
    <div class="modal-content">
      <div class="modal-header text-center">
        <h1 class="modal-title fs-5 w-100" id="staticBackdropLabel">Welcome to Edward's Farms</h1>
        <!-- <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button> -->
      </div>
      <div id="msgInModl" class="modal-body text-center">
        Are you at least 21 years old?
      </div>
      <div class="modal-footer">
        <div id="not21" class="svgFlagCntr LHS">
          <svg class="svgFlags" viewBox="205 265 150 50" xmlns="http://www.w3.org/2000/svg">
            <path d="M 358.2 263 L 204.5 263 L 215.731 288.907 L 204.5 314.815 L 358.2 314.815 Z" fill="grey"/>
            <text x="245px" y="296px" dx="20" dy="2">NO</text>
          </svg>
        </div>
        <div id="over21" class="svgFlagCntr RHS" data-bs-dismiss="modal">
          <svg class="svgFlags" viewBox="208 265 150 50" xmlns="http://www.w3.org/2000/svg">
            <path d="M 204.5 314.815 L 358.2 314.815 L 346.969 288.908 L 358.2 263 L 204.5 263 Z" fill="grey"/>
            <text x="245px" y="296px" dx="10" dy="2">YES</text>
          </svg>
        </div>
      </div>
    </div>
  </div>
</div>

<script type="text/javascript">
// not21 red failure msg
const sorryMsgTxt = "Sorry, you must be 21+ to visit Edward's."
// over21 redir loc for 
const redirLoc  = "{{ '/certificates' | relative_url }}"
const not21Status = false

document.addEventListener('DOMContentLoaded', function() {
  const myModal = new bootstrap.Modal('#staticBackdrop');
  myModal.show();

  function underAger(){
    let not21  = document.getElementById('not21');
    let over21 = document.getElementById('over21');

    not21.addEventListener('click', function() {
      let msgInModl = document.getElementById("msgInModl");
      msgInModl.innerHTML = sorryMsgTxt;
      msgInModl.style.color = "#BA0021";
      msgInModl.style.fontWeight = "500";
      over21.removeAttribute('data-bs-dismiss', 'modal');//comment out to enable the user to simply click over21 w/o page reload
      // export default not21Status
      over21.setAttribute('not21Clicked', 'true');
//      var not21Status = true
      console.log('not21 clicked');
      console.log('over21 OBJ ->' + over21.getAttribute('not21Clicked'));
//      return not21Status
    });
//      console.log('MID ' + not21Status);
    // over21.addEventListener('click', function() {
    //     console.log('SECND ' + not21Status);
    //   if (over21.hasOwnProperty('not21Clicked')){
    //     console.log('THIRD ' + not21Status);
    //     //window.location.replace(redirLoc);
    //   } else {
    //     console.log('4th ' + not21Status);
    //   }
    // });
  }
  underAger();
  function not21Checkr(){
    over21.addEventListener('click', function() {
      if (over21.getAttribute('not21Clicked') == 'true'){
        console.log('YES!! not21Clicked');
      } else {
        console.log('NO not21Clicked');
        window.location = redirLoc;
      }
    });
  }
  not21Checkr();
});
</script>
