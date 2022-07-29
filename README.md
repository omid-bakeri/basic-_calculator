# basic-_calculator
# This web app is a basic calculator create with html , css and javascript


<!DOCTYPE html>
<html lang="en" dir="ltr">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Calculator</title>
        <link rel="stylesheet" href="css/style.css" type="text/css">
    </head>
    <body>
        <div class="main">
            <div class="calc">
                <div id="display"> 0.0 </div>
                    <div id="clear" class="button">C</div>
                    <div id="clear-last-action"  class="button">CE</div>
                    <div id="back-space" class="button"><<</div>
                    <div id="division" class="button">/</div>
                    <div  class="button  btn-number">7</div>
                    <div  class="button  btn-number">8</div>
                    <div  class="button  btn-number">9</div>
                    <div id="multiple" class="button">*</div>
                    <div  class="button  btn-number">4</div>
                    <div  class="button  btn-number">5</div>
                    <div  class="button  btn-number">6</div>
                    <div id="minus" class="button">-</div>
                    <div  class="button  btn-number">1</div>
                    <div  class="button  btn-number">2</div>
                    <div  class="button  btn-number">3</div>
                    <div id="plus" class="button">+</div>
                    <div id="btn-p-n" class="button">+-</div>
                    <div  class="button  btn-number">0</div>
                    <div id="point" class="button">.</div>
                    <div id="equal" class="button" >=</div>
            </div>
        </div>
        <script src="js/main.js"></script>
    </body>
</html>





# css

*{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
body{
    background-color: #022934;
}
.main{
    margin: 0 auto;
    width: 960px;
}
.calc{
    width: 35%;
    height: 65%;
    border: 2px solid black;
    margin: 0 auto;
    background-color: antiquewhite;
    transform: translate(0,30%);
    padding: 10px;
    overflow: hidden;
    border-radius: 5px;
}
#display{
    border: 1px solid black;
    font-size: 1.3em;
    background-color: #dad9d9;
    padding: 10px 5px;
    border-radius: 5px;
    margin-bottom: 20px;
}
.button{
    color: #fff;
    background-color: #232323;
    text-align: center;
    border: 1px solid #a4a4a4;
    border-radius: 15px;
    float: left;
    width: 23.5%;
    margin: 2px;
    height: 50px;
    padding: 14px 5px;
    box-shadow: 1px 1px 2px #000;
    font-size: 1.3em;
    user-select: none;
}
.button:hover{
    cursor: pointer;
    background-color: #6c6c6c;
}
.button:active{
    box-shadow: 1px 1px 5px black inset;
    padding: 12px 5px;
}
#equal{
    background-color: green;
}



# javascript 

let btnDisplay = document.querySelector('#display')
let btnClear = document.querySelector('#clear')
let btnDivision = document.querySelector('#division')
let btnNumbers = document.querySelectorAll('.btn-number')
let btnBackSpace = document.querySelector('#back-space')
let btnMultiple = document.querySelector('#multiple')
let btnMinus = document.querySelector('#minus')
let btnPlus = document.querySelector('#plus')
let btnPN = document.querySelector('#btn-p-n')
let btnPoint = document.querySelector('#point')
let btnEqual = document.querySelector('#equal')

btnClear.addEventListener('click',(e)=>{
    display.textContent="0.0";
    setPoint=false;
});


let setRes = false;
let setPoint = false;

btnNumbers.forEach((item)=>{
    item.addEventListener('click',(e)=>{
        if(display.textContent == "0.0"){
            display.textContent=e.target.textContent;
        }
        else{
            display.textContent += e.target.textContent;
        }
    })
});

btnBackSpace.addEventListener('click',(e)=>{
    let len = display.textContent.length;

    if(len>1){
        display.textContent = display.textContent.substr(0,len-1);
        setPoint=false;
    }
    else{
        display.textContent = "0.0";
        setPoint=false;
    }
});

btnPN.addEventListener('click',(e)=>{
    display.textContent = display.textContent*-1;
});

btnPoint.addEventListener('click',(e)=>{
    if(setPoint == false){
        display.textContent+=".";
        setPoint=true;
    }
});

let number1;
let number2;
let operation = "";

// +
btnPlus.addEventListener('click',(e)=>{
    number1 = Number(display.textContent);
    display.textContent = "0.0";
    operation = "+";
    setPoint = false;
});

// -
btnMinus.addEventListener('click',(e)=>{
    number1 = Number(display.textContent);
    display.textContent="0.0";
    operation = "-";
    setPoint = false;
});

// *
btnMultiple.addEventListener('click',(e)=>{
    number1= Number(display.textContent);
    display.textContent = "0.0";
    operation = "*";
    setPoint = false;
});

// /
btnDivision.addEventListener('click',(e)=>{
    number1 = Number(display.textContent);
    display.textContent = "0.0";
    operation = "/";
    setPoint = false;
});
btnEqual.addEventListener('click',(e)=>{
    // if(setRes==false){
    //     number2 = Number(display.textContent);
    // }
    // else{
    //     number1 = Number(display.textContent);
    // }

    number2 = Number(display.textContent);
    switch(operation){
        case "+":
            let pls = number1 + number2;
            display.textContent = Number(pls);

            break;
        case "-":
            let mus = number1 - number2;
            display.textContent = Number(mus);

            break;
        case '*':
            let mul = number1 * number2;
            display.textContent = Number(mul);

            break;
        case "/":
            let dvi = number1 / number2;
            display.textContent = parseFloat(dvi);

            break;
    }
});

