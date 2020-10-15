<script>
let m = '';
let container;	
let fruits = ["apple","avocado","orange","pineapple","grapes"];
let matches='';
let searches='';	
 function autocomplete(event) {
       searches = event.target.value;
	     matches = fruits.filter(fruit =>{
				 const regex = new RegExp(`^${searches}`,'gi');
				 return fruit.match(regex);
			 });
	   if(searches.length ===0){
			 matches=[];
		 }
    };
function a(ma){
	m = ma;
	matches = [];
}	
</script>
<div class="form-group">
	<input type="text" on:input={autocomplete} placeholder="Enter Name" 
    class="dropdown" value={m}>	
	<div class="dropdown">
	<div id="myDropdown" class="dropdown-content">
		{#each matches as match}
		<li on:click={a(match)}>{match.slice(0,searches.length)}{@html match.slice(searches.length,match.length).bold()}</li>
		{/each}
		</div>
		</div>
	</div>


<style>
	.dropdown :global(.dropdown-content) {
  position: absolute;
  background-color: #f1f1f1;
  min-width: 216px;
  box-shadow: 1px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
  }
	:global(li):hover{background-color: #ddd}
	:global(li){
		color: black;
  padding: 12px 16px;
  text-decoration: none;
	display:block;	
	}
	
</style>
