<script>
  import Dashboard from './components/Dashboard.svelte'
</script>

<svelte:head>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="true" />
  <link
    href="https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<main
  class="w-screen min-h-screen grid place-items-center bg-cstm-neutral-very-dark-blue px-5 py-20"
>
  <Dashboard />
</main>
