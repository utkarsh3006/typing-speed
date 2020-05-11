# typing-speed

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <link href="https://fonts.googleapis.com/css2?family=Alegreya&family=Lobster&family=Pacifico&family=Sriracha&display=swap" rel="stylesheet">
  <style>
  *{ padding: 0; margin: 0; box-sizing: border-box; font-family: 'Lobster', cursive;
font-family: 'Pacifico', cursive;
font-family: 'Alegreya', serif;
font-family: 'Sriracha', cursive;}
  .maindiv{
    width: 100%;
    height:100vh;
    position: relative;
    background: #3498db;
  }
  .centerdiv{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align:center;
  }
  h1{
    text-transform: capitalize;
    margin-bottom: 30px;
    color: #ecf0f1;
    text-shadow: 1px 2px 3px #2980b9;
    font-size: 2.1rem;
  }
  textarea
  {
    background-color: #444;
    box-shadow: 0 0 1px rgba(0,0,0,0.2);
    border-radius: 10px 10px 0 0;
    border: 20px solid #34495e;
    color: white;
  }
  .mainbtn{
padding: 10px 20px;
border-radius: 20px;
border: 5px solid #2980b9;
background-color: #ecf0f1;
font-size: 1rem;
  }
  </style>
</head>
<body>
<div class="maindiv">
  <div class="centerdiv">
    <h1>Welcome To Typing Speed Test</h1>
    <h2 id="msg"></h2>
    <br>
    <textarea name="" id="mywords" cols="100" rows="10" placeholder="Remember, be nice!">
    </textarea>
    <br>
    <button id="btn" class="mainbtn">Start</button>
  </div>
</div>
<script>
  const setOfWords =[
  "Modern humans arrived on the Indian subcontinent from Africa no later than 55,000 years ago.",
  "Their long occupation, initially in varying forms of isolation as hunter-gatherers",
  "Early political consolidations gave rise to the loose-knit Maurya and Gupta Empires based in the Ganges Basin."
];
const msg =document.getElementById('msg');
const typeWords =document.getElementById('mywords');
const btn=document.getElementById('btn');
let startTime, endTime;
const playgame=() =>
{
  let rn=Math.floor(Math.random()*setOfWords.length);
  msg.innerText= setOfWords[rn];
  let date =new Date();
  startTime=date.getTime();
  btn.innerText="Done";
}
const endgame =() =>
{
  let date =new Date();
  endTime=date.getTime();
  let totalTime=((endTime-startTime)/1000);
  console.log(totalTime);
  let totalstr=typeWords.value;
  let wordCount=wordCounter(totalstr);
  let speed= Math.round((wordCount/totalTime)*60);
  let finalmsg= "You typed total at " + speed+ " words per minute ";
  finalmsg+= compareWords(msg.innerText , totalstr);
  msg.innerText=finalmsg;
}
const compareWords =(str1,str2) =>
{
  let words1 =str1.split(" ");
  let words2 =str2.split(" ");
  let cnt=0;
  words1.forEach((item, i) => {
    if(item==words2[i])
    {
      cnt++;
    }
  });
  let errorWords =(words1.length -cnt);
  return ("\n"+cnt+ " correct out of " + words1.length+ " words and the total number of errors are "+ errorWords+".");

}
const wordCounter = (str)=>
{
  let response =str.split(" ").length;
  console.log(response);
  return response;
}
btn.addEventListener('click', function(){
  if(this.innerText=='Start')
  {
    typeWords.disabled =false;
    playgame();
  }
  else if(this.innerText=='Done')
  {
    typeWords.disabled =true;
    btn.innerText="Start";
    endgame();
  }
})
</script>
</body>
</html>
