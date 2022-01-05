<script>
  import Dashboard from './components/Dashboard.svelte'
</script>

<svelte:head>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link
    rel="preconnect"
    href="https://fonts.gstatic.com"
    crossorigin="anonymous"
  />
  <link
    href="https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<main
  class="min-h-screen grid place-items-center bg-cstm-neutral-very-dark-blue px-5 py-20 "
>
  <Dashboard />
</main>

<footer
  class="flex justify-center py-5 font-rubik bg-cstm-neutral-very-dark-blue text-white"
>
  <div class="text-center">
    <p>
      Challenge by
      <a
        href="https://www.frontendmentor.io?ref=challenge"
        target="_blank"
        class="underline">Frontend Mentor</a
      >.
    </p>
    <p>
      Coded by
      <a
        href="https://github.com/waleedmumtaz"
        target="_blank"
        class="font-bold underline">Waleed Mumtaz</a
      >.
    </p>
  </div>
</footer>
