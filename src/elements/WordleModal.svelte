<script>
	import Modal from '../elements/WordleModal.svelte';
  let display = true;
  export let title="Title";
  export let subtitle="Subtitle"; 
  export let titleColor=""; //bootstrap color
  export let subtitleColor=""; //bootstrap color
  // export let buttonText="Submit";
  export let className="bg-gray";
  export let openModal = false;
  const modalHandeller = (event)=>{
    event.key === 'Enter' ? openModal=!openModal:'';
    console.log(event.key, openModal);
  }
</script>

<svelte:window on:keydown={event => modalHandeller(event)} />
<div
  class="body {display
    ? ''
    : 'd-none'} position-absolute top-0 start-0 w-100 h-100  {className}"
  on:click|self={() => {
    display = false;
    openModal = false;
  }}
>
  <div
    class="w-50 shadow-sm bg-white border rounded position-absolute start-25 top-20 "
  >
    <!-- Modal header -->
    <p class="text-center fs-1 m-0 fw-bolder {titleColor} ">{title}!</p>
    <!-- sub header -->
    <p class="text-center fs-4 mb-0 fw-light {subtitleColor}">{subtitle}</p>
    <!-- modal body -->
    <div class="p-2 text-center">
      <slot />
    </div>
    <!-- modal bottom buttons -->
    <div class="d-flex justify-content-end m-2">
      <!-- <div class="btn btn-primary me-2" type="">{buttonText}</div> -->

      <div
        class="btn btn-secondary"
        type=""
        on:click={() => {
          (display = false), (openModal = false);
        }}
      >
        Cancel
      </div>
    </div>
  </div>
</div>

<style>
  .body {
    background-color: #e4e4e42a;
    color: #1414149a;
    backdrop-filter: blur(0.1rem);
  }

  .top-20 {
    top: 20%;
  }
  .start-25 {
    left: 25%;
  }
</style>
