<script lang="ts">

</script>

<navbar>
    <div class="logo-wrapper">
      <img src="/img/logo.png" alt="lbpsb board logo." class="logo">
        <h1>LBPSB<span class="fusion-title">FUSION</span></h1>
    </div>
    <div class="icon-wrapper">
      <img class="icon-lock" src="img/lock.png" alt="grid lock icon">
      <img class="icon-bell" src="img/notification.png" alt="notification bell icon">
      <img class="icon-home" src="img/home.png" alt="home icon">
      <div class="username-wrapper">
        <p>Denzel Abraham Braithwaite</p>
        <svg
        class="arr-down"
        xmlns="http://www.w3.org/2000/svg"
        fill="none" viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
        </svg> 
      </div>
    </div>
  </navbar>

<style>
  navbar {
      position: fixed;
      top: 0;
      color: #fff;
      width: 100vw;
      z-index: 20;
      padding: 1rem;

      display: flex;
      justify-content: space-between;
  }

  navbar h1 {
      font-size: 1.125rem;
      letter-spacing: 0.125rem;
      color: #fff;
  }

  .logo {
    height: 4rem;
    width: 4rem;
  }

  .logo-wrapper {
      display: flex;
      gap: 1rem;
      align-items: center;
  }

  .fusion-title {
    color: #26b0e4;
    font-family: 'Roboto';
  }

  .icon-wrapper {
      display: flex;
      width: 600px;
      justify-content: flex-end;
      align-items: center;
      gap: 3rem;
  }

  .icon-lock {
      width: 1.5rem;
      height: 1.5rem;
  }

  .icon-bell {
      width: 1.5rem;
      height: 1.5rem;
  }
  
  .icon-home {
      width: 1.5rem;
      height: 1.5rem;
  }
  
  .username-wrapper {
      display: flex;
      gap: 0.5rem;
      text-align: center;
      align-items: center;
  }

  .arr-down {
      width: 1rem;
      height: 1rem;
      fill: #fff;
  }
</style>