# Sales-Calculator
Sales calculator to mark up and discount parts
<!DOCTYPE html>
<html>
  <head>
    <title>Kamco Price Calculator</title>
    <style>
      /* For Cell Phone Screens */
      @media screen and (min-width: 480px) {
        #calculator {
          background: yellow;
				}
      }
      /* For Computer screens */
      @media screen and (min-width: 1080px) {
        #calculator {
          text-align: center;
          border-style: solid;
          border-radius: 20px;
          border-width: 8px;
          width: 750px;
          background: yellow;
          margin-left: 550px;
          margin-top: 100px;
        }
        #cost {
          text-align: center;
        }
        #percent {
          text-align: center;
        }
        #kamco {
          border-bottom-style: solid;
          padding-bottom: 20px;
          padding-top: 20px;
          border-width: 8px;
          background: black;
          color: yellow;
        }
        .option1 {
          float: left;
          margin-left: 100px;
        }
        .option2 {
          float: right;
          margin-right: 100px;
        }
        #question1 {
          padding-top: 30px;
        }
      }
    </style>
  </head>
  <body
    background="http://i0.wp.com/www.michellekawka.com/wp-content/uploads/2014/03/0470-KAMCO-2013.jpg?resize=420%2C280"
  >
    <div id="calculator">
      <!--Enter cost of part-->
      <h1 id="kamco">Kamco Lock Solutions Price Calculator</h1>
      <div>
        <div class="option1">
          <input
            class="option1"
            type="radio"
            value="Mark up"
            checked="checked"
            name="option"
          />
          <label for="option1">Mark up</label>
        </div>
        <div class="option2">
          <input class="option2" type="radio" value="Discount" name="option" />
          <label for="option2">Discount</label>
        </div>
        <h1 id="question1">
          <span id="textChangeOne">How much does the part cost?</span>
        </h1>
        <input
          id="cost"
          type="text"
          placeholder="Cost of part"
          onkeyup="totalSell()"
        />
        <!--Enter percentage to mark up-->
        <h1 id="textChangeTwo">What percent would you like to mark this up?</h1>
        <input
          id="percent"
          type="text"
          placeholder="Mark up percentage"
          onkeyup="totalSell()"
        />
        <!--Tip total amount-->
        <h1>
          <span id="textChangeThree">Mark up amount</span>:$<span id="markUp">
            0.00</span
          >
        </h1>
        <h1>Total sell amount: $<span id="total"> 0.00</span></h1>
      </div>
    </div>
    <script>
      //If Marking up
      function totalSell() {
        let a = document.getElementById("cost").value;
        let b = document.getElementById("percent").value;
        if (a.length >= 1) {
          let x = (a * b) / 100;
          x = x.toFixed(2);
          document.getElementById("markUp").textContent = x;
          //Get total sell result
          let sellPrice =
            Number(document.getElementById("cost").value) +
            Number(document.getElementById("markUp").textContent);
          sellPrice = Math.round(100 * sellPrice) / 100;
          sellPrice = sellPrice.toFixed(2);
          document.getElementById("total").textContent = sellPrice;
        }
      }

      //Discounting
      function discounting() {
        document
          .querySelector(".option2")
          .addEventListener("click", function totalDiscount() {
            document.getElementById("textChangeOne").textContent =
              "What is the part's list price?";
            document.getElementById("textChangeTwo").textContent =
              "What percent would you like to discount this?";
            document.getElementById("textChangeThree").textContent =
              "Discount amount";

            let a = document.getElementById("cost").value;
            let b = document.getElementById("percent").value;

            if (a.length >= 1) {
              let x = (a * b) / 100;
              x = x.toFixed(2);
              document.getElementById("markUp").textContent = x;

              let sellPrice =
                Number(document.getElementById("cost").value) -
                Number(document.getElementById("markUp").textContent);
              sellPrice = Math.round(100 * sellPrice) / 100;
              sellPrice = sellPrice.toFixed(2);
              document.getElementById("total").textContent = sellPrice;
            }
          });
      }

      function marking() {
        document
          .querySelector(".option1")
          .addEventListener("click", function totalMark() {
            document.getElementById("textChangeOne").textContent =
              "How much does the part cost?";
            document.getElementById("textChangeTwo").textContent =
              "What percent would you like to mark this up?";
            document.getElementById("textChangeThree").textContent =
              "Mark up amount";

            let a = document.getElementById("cost").value;
            let b = document.getElementById("percent").value;
            //Get mark up result
            if (a.length >= 1) {
              let x = (a * b) / 100;
              x = x.toFixed(2);
              document.getElementById("markUp").textContent = x;
              //Get total sell result
              let sellPrice =
                Number(document.getElementById("cost").value) +
                Number(document.getElementById("markUp").textContent);
              sellPrice = Math.round(100 * sellPrice) / 100;
              sellPrice = sellPrice.toFixed(2);
              document.getElementById("total").textContent = sellPrice;
            }
          });
      }

      window.onload = function() {
        discounting();
        marking();
      };
    </script>
  </body>
</html>
