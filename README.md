# CSP-Building-an-App-Canvas-Painter
Lesson 17: Canvas Painter Code Practice
setActiveCanvas("canvas");
setStrokeColor("rgba(0,0,0,0)");
setFillColor("rgba(0,0,0,0.2)");
var eventList = [];
onEvent("canvas", "mousemove", function( event) {
  if (event.shiftKey) {
    appendItem(eventList, event);
    circle(event.offsetX, event.offsetY, dotRadius(event.movementX,event.movementY));
  }
});
onEvent("startOver", "click", function(event) {
  clearCanvas();
  eventList = [];
  console.log("startOver clicked!");
});
onEvent("random", "click", function(event) {
  clearCanvas();
  console.log("random clicked!");
  for (var I = 0; I < eventList.length; I++) {
    circle(eventList[I].offsetX, eventList[I].offsetY, randomNumber(1, 10));
  }
});
onEvent("original", "click", function( ) {
  clearCanvas();
  console.log("random clicked!");
  for (var I = 0; I < eventList.length; I++) {
    circle(eventList[I].offsetX, eventList[I].offsetY, dotRadius(eventList[I].movementX,eventList[I].movementY));
  }
});
function dotRadius(changeX, changeY){
  var speed=Math.abs(changeX)+Math.abs(changeY);
  var output=3+8/speed;
  return output;
}
onEvent("sprayPaint", "click", function( ) {
  clearCanvas();
  console.log("random clicked!");
  for (var I = 0; I < eventList.length; I++) {
    for (var x = 0; x < 5; x++) {
      circle(eventList[I].offsetX + randomNumber(-3,3), eventList[I].offsetY+randomNumber(-3,3), 1);
    }
  }
});
onEvent("etch.button", "click", function(event) {
  clearCanvas();
  setStrokeColor("black");
  for (var I = 0; I < eventList.length-10; I++) {
    line(eventList[I].offsetX, eventList[I].offsetY, eventList[I+10].offsetX, eventList[I+10].offsetY);
  }
  setStrokeColor("rgba(0,0,0,0");
  console.log("etch.button clicked!");
});
onEvent("colorMenu", "change", function( ) {
  setFillColor(getText("colorMenu"));
});
