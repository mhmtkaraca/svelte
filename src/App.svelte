<script>
import Modal from './Modal.svelte';
let string=""
console.log(string)
let show=false;
let isForm=false;

const toggleShow=()=>{
	show=!show;
}
	

	/*export let name="Harun";
	let surname = "asd"

$: fulname=`${name} ${surname}`;
console.log(fulname)
$: console.log(name)

const handleClick = () => {
	if(surname==="asd")
	surname="karaca"
	else
	surname="asd"
}

const handleChange=(e)=>{

	name=e.target.value
}*/

 let people=[

	{name:"Mehmet",surname:"karaca",age:33,city:"Esk",id:1},
	{name:"Mustafa",surname:"karaca",age:33,city:"Ank",id:2},
	{name:"ahmet",surname:"karaca",age:33,city:"Hull",id:3}
	]
	function test(){
		console.log(arguments[2])

	}
	const handleClick = (id)=>{
			
		people=people.filter((person)=>person.id!=id)
		
	}
$: num=0;
</script>



<Modal {isForm} {handleClick} {show} on:click={toggleShow}>
	<div slot="delete">
	<p>{num} idli itemı silmeye Emin misin</p>
    <div>
    <button class="button1" on:click={()=>{handleClick(num)
	toggleShow()
	}}>Evet</button>
    <button class="button1" on:click={toggleShow()}>Hayır</button>
    </div>
</div>
<div slot="form">
	<form on:submit|preventDefault>
		<input type="text" name="name" placeholder="name" />
		<input type="text" name="surname" placeholder="surname" />
		<input type="text" name="age" placeholder="age" />
		<input type="text" name="city" placeholder="city" />
		<button type="submit">Add</button>	
	</form>

</div>
	

</Modal>




<main>
	<button on:click={()=>{isForm=!isForm
	toggleShow()
	}}>Add person</button>

	<div class="alan">
{#each people as {city,name,surname,age,id},index }
	<div class:test={index%2==0} >
	<h1>{city}</h1>
	{#if name==="Mehmet"}
	<div>Merhaba {name}</div>
	{/if}
	<div class="harun">{name} {surname} {age} </div>
	<button on:click={()=>{
		num=id
		isForm=!isForm
		toggleShow()
		console.log(num,show,isForm)
	}}>delete</button>
	</div>
	{:else}
	<div>yok</div>
{/each}


	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	.test {
		background-color:yellow;
		}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>