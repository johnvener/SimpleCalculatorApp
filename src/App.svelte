<script>
	let total = 0;
	let inputField = "";
	let lastState = null;

	function prevState() {
		switch(lastState){
			case "add":
				total += parseFloat(inputField);
				inputField = "0";
				break;
			case "subtract":
				total -= parseFloat(inputField);
				inputField = "0";
				break;
			case "multiply":
				total *= parseFloat(inputField);
				inputField = "0";
				break;
			case "divide":
				total /= parseFloat(inputField);
				inputField = "0";
				break;
			default:
				total = parseFloat(inputField);
				inputField = "0";
				break;
		}
	}
	function setOperation(operation){
		prevState();
		lastState = operation;
	}

	function setValue(value) {
		if(inputField.toString() =="0" || lastState == "equal") {
			inputField = "";
		}
		if(lastState == "equal") {
			lastState = null;
		}
		if(value == "C") {
			total = 0;
			lastState = null;
			inputField = "";
			return;
		}
		 inputField += value;
	}

	
	function totalNum() {
		prevState();
		inputField = total;
		lastState = "equal";
	}

  </script>
  
  <main>
	 <h1> Simple Calculator App </h1>
		<div class = "calculator"> <!--calculator starts here-->
			<input tpye="text" bind:value={inputField} readonly="true"/> 
			<div class="buttons"> <!--buttons starts here-->
				<div class="operations">
					<button on:click={()=>{setOperation('add');}}> + </button>
					<button on:click={()=>{setOperation('subtract');}}> - </button>
					<button on:click={()=>{setOperation('multiply');}}> * </button>
					<button on:click={()=>{setOperation('divide');}}> / </button>
				</div> <!--operations ends here-->
				<div class="numberButtons">
					<div> 
					<button on:click={()=>{setValue(7);}}> 7 </button>
					<button on:click={()=>{setValue(8);}}> 8 </button>
					<button on:click={()=>{setValue(9);}}> 9 </button>
				</div>
					<div>
						<button on:click={()=>{setValue(4);}}> 4 </button>
						<button on:click={()=>{setValue(5);}}> 5 </button>
						<button on:click={()=>{setValue(6);}}> 6 </button>
					</div>
					<div>
						<button on:click={()=>{setValue(1);}}> 1 </button>
						<button on:click={()=>{setValue(2);}}> 2 </button>
						<button on:click={()=>{setValue(3);}}> 3 </button>
					</div>
					<div>
						<button on:click={()=>{setValue(0);}}> 0 </button>
						<button on:click={()=>{setValue('.');}}> . </button>
						<button on:click={()=>{setValue('C');}}> C </button>
					</div>

				</div><!--numberButtons ends here-->
				<div class = "equal" >
					<button on:click={totalNum} > = </button>
				</div> <!--equals ends here-->
				
			</div><!--buttons ends here-->
		</div> <!--calculator ends here-->
  </main>
  
  <style>

	h1{
		text-align: center;
		margin-top: 40px;
	}
	.calculator {
		position: absolute;
		top: 35%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 300px;
		border: 1px solid black;
		box-shadow: 2px 2x 2px #eee;
		padding: 10px;
	}

	.calculator input {
		width: 100%;
		padding: 20px;
		outline: none;
		text-align: right;
		font-size: 20px;
	}
	.calculator .buttons {
		display: flex;
		flex-wrap: wrap;
	}
	.calculator .buttons .operations {
		display: flex;
		justify-content: space-between; 
		width: 100%;
	}
	
	.calculator .buttons .operations button{
		width: 24%;
	}
	.calculator .buttons .numberButtons{
		width: 75%;
	}
	.calculator .buttons .numberButtons > div{
		display: flex;
		justify-content: space-between;
	}
	.calculator .buttons .numberButtons > div button{
		width: 32%;
	}
	.calculator .equal{
		flex: 1;
	}
	.calculator .equal button{
		margin-left:  5%;
		width: 95%;
		height: 95%;
		background-color: aqua;
	}
  </style>
	
