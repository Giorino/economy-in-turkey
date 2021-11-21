<script>
	import {asgariUcret} from "./prices";

	let index = 0;

	$: current = asgariUcret[index];
	$: percent = ((current.price/ current.dollar) / current.price) * 100;
	
const increase = () => {
	if(index < asgariUcret.length -1){
		index++;
	}else{
		index = 0;
	}
}

function numberFormat(number) {
	return new Intl.NumberFormat('tr-TR', {
		maximumSignificantDigits: 4
	}).format(number)
}

setInterval(increase, 1000);

</script>
<div class="container">
	<h3>
		<div class="key">Yıl</div>
		<div class="value">
			{current.year}
		</div>
	</h3>
	<h3>
		<div class="key">Asgari Ücret</div>
		 <div class="value">
			 {current.price}
		</div>
	</h3>
	<h3><div class="key">Dolar Karşılığı</div>
		<div class="value">
			{numberFormat(current.price / current.dollar)}
		</div>
	</h3>
</div>

<div id="percentage" style={`--width: ${percent}%`}>

	<h3>
		ALIM 
    </h3>
	<h3>
		GÜCÜ
	</h3>
	<div>
		%{numberFormat(percent)}
	</div>
</div>

<style>
	*{
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}
	body{
		background-color: black;
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
	}

	.container{
		color: #363636;
		position: absolute;
		top: 0;
		left: 0;
		padding: 20px;
		z-index: 1;
		display: grid;
		gap: 40px;
	}

	#percentage{
		color: #363636;
		width: var(--width, 100%);
		height: 100%;
		background: #85bb65;
		position: absolute;
		top: 0;
		left: 0;
		transition: 1s;
		display: flex;
		flex-direction: column;
		justify-content: flex-end;
		padding: 20px;
	}
	#percentage h3{
		font-weight: 800;
		font-size: 2rem;
	}
	#percentage div{
		font-weight: 700;
		font-size: 1.5rem;
	}

	.container .key{
		font-size: 1rem;
		font-weight: 700;
		margin-bottom: 4px;
	}
	.container .value{
		font-size: 1.5rem;
		font-weight: 800;
	}
	
</style>