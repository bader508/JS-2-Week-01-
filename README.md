# JS-2-Week-01-
<!DOCTYPE html>
<html lang="en">
      
<head>
   <style type="text/css">
        *{
            margin:0;
            padding:0;
        }
        body  {
                 
    line-height: 35px;
    font-family: f-webkit-pictograph;
    font-size: 25px;
    font-weight:bolder;
       
    
    }
    #background-cover {
  position: fixed;
  
  top: 0;
  overflow: hidden;
  left: 0;
 
   }  
    h1{
        text-align: center;
       margin:2%;
    }
    p{
        margin-top: 2%;
        letter-spacing: 5px;
        color: #a3d2e4;
      
    }

    .background-cover{
        position:absolute;
        z-index:-1 ;
        }
       
    </style>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>JS2/Week-01_Randomecars</title>
    
</head>

<body>
    <div class="background-cover">
        <video id="background-cover" preload="auto" autoplay="true" loop="loop" muted="muted" width="100%">
            <source src="VIDEO.mp4" type=video/mp4>
                video not supported 
        </video>
    </div>
       
    <div id="content" >
    <h1 style="color:rgb(2, 1, 1)">Given tasks:</h1><hr>
    <p>
    Use the carGenerator function to generate 10 cars. <br>The file with the function is here:    
    <a href="https://github.com/HackYourFuture-CPH/JavaScript/blob/master/Week4/code/carGenerator.js">"https://github.com/HackYourFuture-CPH/JavaScript/blob/master/Week4/code/carGenerator.js"</a><br>
    You call it like this: generateCars(10);
    Create the following arrays:<br>
    1.1: Cars with speeds between 30 and 60<br>
     1.2: The makes of the cars that are not lightyellow, so the array is going to look like this: ['BMW', 'Fiat'] etc<br>
     1.3: Lets change the cars array so it can be read by a danish person. Return an array of objects where the key in the object called speed is called fart (danish for speed), the make is called maerke and the color is called farve. The output will look kind of like this:<br>
          [
                {
                    <br>maerke: 'Volvo',<br>
                    fart: 45,<br>
                    farve: 'lightYellow',<br>
                }
            ];
        </p>
    </div>
    <script>
            let message="Please check the console for code"
            alert(message);
            /**
 * Get random integer between two numbers, found here: https://stackoverflow.com/a/7228322
 * @param {integer} min - The min number
 * @param {integer} max - The max number
 * @returns {Number} Random number between min and max
 */
    function randomIntFromInterval(min, max) {
    return Math.floor(Math.random() * (max - min + 1) + min);
}


/**
 * Get an array with car objects with random color and speed
 * @param {integer} numberOfCars - The number of cars 
 * @returns {array} Array containing the car objects
 */
    function generateCars(numberOfCars) {
    const cars = [];

    const carMakes = ['Honda', 'BMW','Fiat','Skoda','Volvo'];
    const carColors = ['lightgrey', 'lightcyan','lightyellow','lightgreen','lightcoral','lightpink'];
    
    for (let i = 0; i < numberOfCars; i++) {
        const car = {};
        const randomMakeIndex = randomIntFromInterval(0, carMakes.length - 1);
        const randomColorIndex = randomIntFromInterval(0, carColors.length - 1);

        car.make = carMakes[randomMakeIndex];
        car.color = carColors[randomColorIndex];
        car.speed = randomIntFromInterval(0, 100);

        cars.push(car);
    }

    return cars;
}




//  Generate 10 random cars
const cars = generateCars(10);
console.log("10 Random cars:");
console.log(cars);

// 1.1  Cars with speeds between 30 and 60

 const Speed = cars.filter(car => car.speed > 30 && car.speed < 60);
console.log('Cars with speeds between 30 and 60');
console.log(Speed);



// 1.2  The make of the cars that are not lightyellow
// 1.2  i am not able to filter cars with only color. it shows me make of cars and speed too which i don't want.
function getMakeOfCar(car) {
	return car.color;
}
const Color = cars.filter(car => car.color !== "lightyellow");

console.log("List that exclude lightyellow cars");
console.log(Color);



// 1.3  Change the array to a specified format

function convertArrayToDanish(car) {
  return {
    maerke: car.make,
    fart: car.speed,
    farve: car.color  
  } 
}
console.log("New Array in Danish");
console.log(cars.map(convertArrayToDanish));


            
        </script>
       
</body>

