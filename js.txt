

$(document).ready(function(){
  //store the inputs from the user
  var inputs = [""];
  //string to store the current input string
  var totalString;
  //validation array without the.
  var operators1 = ["+", "-", "/", "*"];
  //operators array with the. for validation
  var operators2 = ["."];
  //numbers for validation
  var nums = [0,1,2,3,4,5,6,7,8,9];
  
  function update(){
    totalString = inputs.join("");
    $("#steps").html(totalString);
    console.log(inputs);
  }
  
  function getValue(input){
    if(operators2.includes(inputs[inputs.length-1]) && input === "."){
      console.log("duplicate '.' ");
    }
    else if(inputs.length === 1 && !operators1.includes(input) ){
      inputs.push(input);
    }
    else if(!operators1.includes(inputs[inputs.length-1])){
      inputs.push(input);
    }
    else if(nums.includes(Number(input))){
      inputs.push(input);
    }
    update();
  }
  
  
  
  function getTotal(){
    totalString = inputs.join("");
    $("#steps").html(eval(totalString));
  }
  
  $("a").on("click",function(){
    if(this.id === "deleteAll"){
      inputs = [""];
      update();
    }
    else if(this.id === "backOne"){
      inputs.pop();
      update();
    }
    else if(this.id === "equal"){
      getTotal();
    }
    else {
           getValue(this.id);
         }
    
  });
});