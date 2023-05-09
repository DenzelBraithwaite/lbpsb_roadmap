<script lang="ts">
    let src = 'public/images/logo.png';
  </script>
  
<navbar>
    <div class="nav-logo-group">
      <img {src} alt="lbpsb board logo.">
        <h1>LBPSB<span class="fusion-title">FUSION</span></h1>
    </div>
    <div class="nav-tools-group">
      <img class="nav-icon-lock" src="images/lock.png" alt="grid lock icon">
      <img class="nav-icon-bell" src="images/notification.png" alt="notification bell icon">
      <img class="nav-icon-home" src="images/home.png" alt="home icon">
      <div class="nav-username-group">
        <p>Denzel Abraham Braithwaite</p>
            <svg
            class="arr-down"
            xmlns="http://www.w3.org/2000/svg"
            fill="none" viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor">
            <path stroke-linecap="round"
            stroke-linejoin="round"
            d="M19.5 8.25l-7.5 7.5-7.5-7.5" 
            />
        </svg> 
      </div>
    </div>
  </navbar>

  <style>
    navbar {
        /* position: fixed; */
        z-index: 20;
        margin-left: auto;
        margin-right: auto;
        padding-top: 0.5rem;
        width: 95%;
        display: flex;
        justify-content: space-between;
        height: 3.5rem;
        margin-bottom: 5rem;
    }

    navbar h1 {
        font-size: 18px;
        letter-spacing: 2px;
        color: #fff;
        font-weight: 400;
    }

    .nav-logo-group {
        display: flex;
        gap: 1rem;
    }
  
    .fusion-title {
      color: #26b0e4;
      font-family: 'Roboto';
    }

    .nav-tools-group {
        display: flex;
        width: 600px;
        justify-content: flex-end;
        align-items: center;
        gap: 3rem;
    }

    .nav-icon-lock {
        width: 1.5rem;
        height: 1.5rem;
    }

    .nav-icon-bell {
        width: 1.5rem;
        height: 1.5rem;
    }
    
    .nav-icon-home {
        width: 1.5rem;
        height: 1.5rem;
    }
    
    .nav-username-group {
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