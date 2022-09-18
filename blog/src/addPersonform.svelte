<script>
    import {createEventDispatcher} from 'svelte';
    let dispatch = createEventDispatcher();
    let name;
    let beltColour;
    let age;
    let skills = []

    const handleSubmit =()=>{
       const person = {
        name,
        beltColour,
        age,
        skills:skills,
        id:Math.random()
       }
       dispatch('addPerson', person);
    }
</script>

<h3>Add a new person</h3>
<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name}>
  <input type="number" placeholder="age" bind:value={age}>

  <!-- svelte-ignore a11y-label-has-associated-control -->
  <label>Skills:</label>
  <input type="checkbox"bind:group={skills} value="fighting"> fighting 
  <input type="checkbox"bind:group={skills} value="sneeking" > sneeking 
  <input type="checkbox"bind:group={skills} value="running"> running <br>
  <!-- svelte-ignore a11y-label-has-associated-control -->
  <label> beltcolour</label>
  <select bind:value={beltColour}>
    <option value="black">black</option>
    <option value="orange">orange</option>
    <option value="brown">brown</option>
    <option value="white">white</option>
  </select>
  <button>Add Person</button>
</form>

<style>

</style>