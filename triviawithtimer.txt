$(document).ready(function() {

        var correct = 0;
        var incorrect = 0;
        var counter = 0;
        var timeLeft = 30;
        var x = 0;
      

       var game = {
        questionCounter: 0,
        trivia: [

            {
                question: "when was the first winter olympics?",
                answer: "1924",
                choices: [
                    "160",
                    "1600",
                    "1900",
                    "1924",
                ]
            },

            {
                question: "name one paralympic althlet from PChang 2018 winter OLYMPICS?",
                answer: "Jasmin Bambur",
                choices: [
                    "Jasmin Bambur",
                    "Dantooine",
                    "Nar Shadaa",
                    "Yavin",
                ]
            },

            {
                question: "how many medals did Mikaela Schiffrin win in 2018 Olympics?",
                answer: "2",
                choices: [
                    "2",
                    "3",
                    "4",
                    "10",
                ]
            },

            {
                question: "WHo is lindsey VOnn",
                answer: "ski alpine athlete",
                choices: [
                    "dancer",
                    "ski alpine athlete",
                    "golfer",
                    "coder",
                ]
            }
        ]
    }


    





      function timerSetup() {


         counter = 0;
         timeLeft = 30;


        $(".timer").text(timeLeft-counter);


function timeIt() {
    counter ++;
 
    $(".timer").text(timeLeft-counter);



    if ((timeLeft-counter) <= 0) {
        clearInterval(x);
    
        alert("Out of time... incorrect");
        incorrect++;
    
        game.questionCounter ++;
        displayWinsLosses();
      
        
        startGame();
    
    }



}

 x = setInterval (timeIt, 1000);




      }











      startGame();



      

      function displayWinsLosses() {
        $(".wins").text("You have guessed " + correct + " question(s) correctly");
      $(".losses").text("You have guessed " + incorrect + " question(s) incorrectly");

      }

      function clearQuestionsAnswers() {
        $(".choices").empty();
        $(".question").empty();


      }

      function startGame() {
        clearInterval(x);
        clearQuestionsAnswers();
        timerSetup();
        
        

     

        if (game.questionCounter === game.trivia.length) {
            
            $(".question").text("Game Complete!");

            displayWinsLosses();
            
        }

        

          $(".question").text(game.trivia[game.questionCounter].question)
          for (let i=0; i < game.trivia[game.questionCounter].choices.length; i++) {

            var p = $("<button>").text(game.trivia[game.questionCounter].choices[i]).attr("id", game.trivia[game.questionCounter].choices[i])
            p.addClass("optionsOf btn btn-primary btn-rounded")

            $(".choices").prepend(p)

 
       
            




      


     
           
          }



        }

        $(document).on("click", ".optionsOf", function(){
        // $(".optionsOf").on("click", function() {]
       
            console.log("click")


var guess = ($(this).attr("id"));

console.log("you guessed " + guess);
console.log("answer is " + game.trivia[game.questionCounter].answer);



if (guess === game.trivia[game.questionCounter].answer) {
   
      alert("Correct!")
      correct ++;
      game.questionCounter ++;
      displayWinsLosses();
      

     
      startGame();

    }
    else  {
       
        alert("Incorrect");
      incorrect++;
      game.questionCounter ++;
      displayWinsLosses();
 
 
      startGame();

    }

});
});






        


      
    




      
    