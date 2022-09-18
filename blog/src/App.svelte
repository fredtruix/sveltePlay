<script>

  import Modal from './modal.svelte';
  import PersonForm from './addPersonform.svelte';
  let showModal = false;
  const toggleModal = ()=>{
    showModal = !showModal;
  }

  let people = [
    { name: 'yoshi', beltColour: 'black', age: 25, id: 1 },
    { name: 'mario', beltColour: 'orange', age: 45, id: 2 },
    { name: 'luigi', beltColour: 'brown', age: 35, id: 3 }
  ];

  const handleDelete = (id)=>{
    people = people.filter((person)=>person.id != id)
  }

  let num = 15;
  const addPerson =(e)=>{
    const person = e.detail;
    people = [person, ...people]
    showModal = false;
  }
</script>


<Modal  {showModal} on:click={toggleModal}>
  <PersonForm on:addPerson={addPerson}/>
</Modal>
<main>
  <button on:click={toggleModal}>Open Modal</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColour === "black"}
      <h2>MASTER NINJA</h2>
      {/if}
      <p>{person.age} years old, {person.beltColour} belt</p>
      <button on:click={()=>handleDelete(person.id)}>delete</button>
    </div>
    {:else}
    <p>There are Know people to show</p>
  {/each}


</main>

<style>

main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
