<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a href="/" class="navbar-brand my-logo" id="banner">
          <img class="lctec-logo-img" src="../src/assets/images/3logo.webp" alt="LC Tech logo">          
      </a>
      <a @click="hamburgerClicked = !hamburgerClicked"
          role="button" 
          class="my-burger" 
          aria-label="menu" 
          aria-expanded="false" 
          data-target="my-navbar-menu" 
          v-bind:class="{'is-active':hamburgerClicked}">
          <div :class="$store.state.theme_change" >
            <span aria-hidden="true"></span>
            <span aria-hidden="true"></span>
          </div>
      </a>
    </div>  
    <!-- hamburger menu -->
    <div class="my-navbar-menu" 
      id="my-navbar-menu"
      v-bind:class="{'is-active':hamburgerClicked}"
      :style="hamburgerClicked === true ? 'width: 100%; background-color: ' + $store.state.hamburgerBgColor : 'width: ' + closeNav">
      <div 
        class="navbar-end"
        v-bind:class="{'is-active':hamburgerClicked}">
        <div class="navbar-item my-theme-switch">
          <button @click="toggleTheme()" class="theme-toggle">
              <div>
                <i v-if="$store.state.isDarkTheme" class="gg-moon fa fa-moon theme-icon-when-dark"></i>
                <svg v-else-if="!$store.state.isDarkTheme" xmlns="http://www.w3.org/2000/svg" width="26" height="26" fill="currentColor" class="gg-sun theme-icon-when-light" viewBox="0 0 16 16">
                  <path d="M8 11a3 3 0 1 1 0-6 3 3 0 0 1 0 6m0 1a4 4 0 1 0 0-8 4 4 0 0 0 0 8M8 0a.5.5 0 0 1 .5.5v2a.5.5 0 0 1-1 0v-2A.5.5 0 0 1 8 0m0 13a.5.5 0 0 1 .5.5v2a.5.5 0 0 1-1 0v-2A.5.5 0 0 1 8 13m8-5a.5.5 0 0 1-.5.5h-2a.5.5 0 0 1 0-1h2a.5.5 0 0 1 .5.5M3 8a.5.5 0 0 1-.5.5h-2a.5.5 0 0 1 0-1h2A.5.5 0 0 1 3 8m10.657-5.657a.5.5 0 0 1 0 .707l-1.414 1.415a.5.5 0 1 1-.707-.708l1.414-1.414a.5.5 0 0 1 .707 0m-9.193 9.193a.5.5 0 0 1 0 .707L3.05 13.657a.5.5 0 0 1-.707-.707l1.414-1.414a.5.5 0 0 1 .707 0m9.193 2.121a.5.5 0 0 1-.707 0l-1.414-1.414a.5.5 0 0 1 .707-.707l1.414 1.414a.5.5 0 0 1 0 .707M4.464 4.465a.5.5 0 0 1-.707 0L2.343 3.05a.5.5 0 1 1 .707-.707l1.414 1.414a.5.5 0 0 1 0 .708"/>
                </svg>
              </div>
          </button>
        </div>
        <!-- services -->
        <div class="navbar-item my-dropdown" data-dropdown-services>
          <button :class="$store.state.theme_change" class="my-link" @click="hamburgerClicked = false; scrollTo('offering')" style="font-weight: 700;" data-dropdown-button-services>
              {{$t('whatweoffer')}}
          </button>
          <div class="my-dropdown-menu">
            <div class="my-dropdown-links">
              <a class="my-link my-dropdown-item" @click="hamburgerClicked = false; scrollTo('ecommerce')">
                {{$t('eCommerce')}}
                  <svg 
                    class="dropdown-arrow-icon"
                    xmlns="http://www.w3.org/2000/svg" 
                    aria-hidden="true" 
                    focusable="false" 
                    height="24px" 
                    viewBox="0 0 24 24" 
                    width="24px">
                    <path d="M0 0h24v24H0V0z" fill="none"></path>
                    <path d="M9 5v2h6.59L4 18.59 5.41 20 17 8.41V15h2V5H9z"></path>
                  </svg>                        
              </a>
              <a class="my-link my-dropdown-item" @click="hamburgerClicked = false; scrollTo('webapp')">
                {{$t('web_design')}}
                  <svg 
                    class="dropdown-arrow-icon"
                    xmlns="http://www.w3.org/2000/svg" 
                    aria-hidden="true" 
                    focusable="false" 
                    height="24px" 
                    viewBox="0 0 24 24" 
                    width="24px">
                    <path d="M0 0h24v24H0V0z" fill="none"></path>
                    <path d="M9 5v2h6.59L4 18.59 5.41 20 17 8.41V15h2V5H9z"></path>
                  </svg>                            
              </a>
              <a class="my-link my-dropdown-item" @click="hamburgerClicked = false; scrollTo('gensoft')">
                {{$t('gensoftdev')}}
                  <svg 
                    class="dropdown-arrow-icon"
                    xmlns="http://www.w3.org/2000/svg" 
                    aria-hidden="true" 
                    focusable="false" 
                    height="24px" 
                    viewBox="0 0 24 24" 
                    width="24px">
                    <path d="M0 0h24v24H0V0z" fill="none"></path>
                    <path d="M9 5v2h6.59L4 18.59 5.41 20 17 8.41V15h2V5H9z"></path>
                  </svg>                            
              </a>
            </div>
          </div>
        </div>
        <!-- contact -->
        <div class="navbar-item my-dropdown">
          <button :class="$store.state.theme_change" class="my-link" style="font-weight: 700;" @click="hamburgerClicked = false; scrollTo('contact')">
            {{$t('contact')}}                         
          </button>          
        </div> 
        <!-- locale change -->
        <div class="navbar-item my-dropdown" data-dropdown>
          <button class="my-link" data-dropdown-button>
            <svg 
            :class="$store.state.theme_change"
              class="locales-btn-icon" 
              xmlns="http://www.w3.org/2000/svg" 
              aria-hidden="true" 
              focusable="false" 
              viewBox="0 0 24 24">
              <path 
                d="M0 0h24v24H0z" 
                fill="none">
              </path>
              <path 
                d=" M12.87 15.07l-2.54-2.51.03-.03c1.74-1.94 2.98-4.17 3.71-6.53H17V4h-7V2H8v2H1v1.99h11.17C11.5 7.92 10.44 9.75 9 11.35 8.07 10.32 7.3 9.19 6.69 8h-2c.73 1.63 1.73 3.17 2.98 4.56l-5.09 5.02L4 19l5-5 3.11 3.11.76-2.04zM18.5 10h-2L12 22h2l1.12-3h4.75L21 22h2l-4.5-12zm-2.62 7l1.62-4.33L19.12 17h-3.24z ">
              </path>
            </svg>                        
          </button>
          <div class="my-dropdown-menu">
            <div class="my-dropdown-links">
              <!-- region button -->
              <a class="my-link my-dropdown-item" @click="changeLanguageButton('en')">
                  English
                  <svg 
                    class="dropdown-arrow-icon"
                    xmlns="http://www.w3.org/2000/svg" 
                    aria-hidden="true" 
                    focusable="false" 
                    height="24px" 
                    viewBox="0 0 24 24" 
                    width="24px">
                    <path d="M0 0h24v24H0V0z" fill="none"></path>
                    <path d="M9 5v2h6.59L4 18.59 5.41 20 17 8.41V15h2V5H9z"></path>
                  </svg>                        
              </a>
              <a class="my-link my-dropdown-item" @click="changeLanguageButton('ja')">
                  日本語
                  <svg 
                    class="dropdown-arrow-icon"
                    xmlns="http://www.w3.org/2000/svg" 
                    aria-hidden="true" 
                    focusable="false" 
                    height="24px" 
                    viewBox="0 0 24 24" 
                    width="24px">
                    <path d="M0 0h24v24H0V0z" fill="none"></path>
                    <path d="M9 5v2h6.59L4 18.59 5.41 20 17 8.41V15h2V5H9z"></path>
                  </svg>                            
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
  <div class="content-wrapper">
    <router-view/>
  </div>
  		<!-- Footer only stays at the bottom in this file, not App.vue-->
      <footer class="my-footer">          
        <div class="location-beacon">
          <div class="circle"></div>
          <div style="display: block;">
            <p style="font-size: 12px; padding: 0.1rem;">
              {{$t('Current_Location')}}: {{ userCountry }}
            </p>
            <p style="font-size: 12px; padding: 0.1rem; float:left">
              {{$t('Your_IP')}}: {{ userIP }}
            </p>
          </div>
        </div>     
        <!-- SNS icons -->
        <div class="social-media-div">
          <ul class="sns">
            <!-- <li class="apple">
              <a 
                class="icon apple" 
                rel="noopener" 
                target="_blank" 
                title="https://music.apple.com/us/artist/sheriff-crandy/1583455144"
                href="https://music.apple.com/us/artist/sheriff-crandy/1583455144">
                <svg 
                xmlns="http://www.w3.org/2000/svg" 
                width="25" 
                height="25" 
                class="apple-svg" 
                viewBox="0 0 16 16">
                  <path
                    d="M11.182.008C11.148-.03 9.923.023 8.857 1.18c-1.066 1.156-.902 2.482-.878 2.516.024.034 1.52.087 2.475-1.258.955-1.345.762-2.391.728-2.43Zm3.314 11.733c-.048-.096-2.325-1.234-2.113-3.422.212-2.189 1.675-2.789 1.698-2.854.023-.065-.597-.79-1.254-1.157a3.692 3.692 0 0 0-1.563-.434c-.108-.003-.483-.095-1.254.116-.508.139-1.653.589-1.968.607-.316.018-1.256-.522-2.267-.665-.647-.125-1.333.131-1.824.328-.49.196-1.422.754-2.074 2.237-.652 1.482-.311 3.83-.067 4.56.244.729.625 1.924 1.273 2.796.576.984 1.34 1.667 1.659 1.899.319.232 1.219.386 1.843.067.502-.308 1.408-.485 1.766-.472.357.013 1.061.154 1.782.539.571.197 1.111.115 1.652-.105.541-.221 1.324-1.059 2.238-2.758.347-.79.505-1.217.473-1.282Z"/>
                  <path 
                    d="M11.182.008C11.148-.03 9.923.023 8.857 1.18c-1.066 1.156-.902 2.482-.878 2.516.024.034 1.52.087 2.475-1.258.955-1.345.762-2.391.728-2.43Zm3.314 11.733c-.048-.096-2.325-1.234-2.113-3.422.212-2.189 1.675-2.789 1.698-2.854.023-.065-.597-.79-1.254-1.157a3.692 3.692 0 0 0-1.563-.434c-.108-.003-.483-.095-1.254.116-.508.139-1.653.589-1.968.607-.316.018-1.256-.522-2.267-.665-.647-.125-1.333.131-1.824.328-.49.196-1.422.754-2.074 2.237-.652 1.482-.311 3.83-.067 4.56.244.729.625 1.924 1.273 2.796.576.984 1.34 1.667 1.659 1.899.319.232 1.219.386 1.843.067.502-.308 1.408-.485 1.766-.472.357.013 1.061.154 1.782.539.571.197 1.111.115 1.652-.105.541-.221 1.324-1.059 2.238-2.758.347-.79.505-1.217.473-1.282Z"/>
                </svg>
              </a>
            </li> -->
            <!-- <li class="spotify">
              <a 
                class="icon spotify" 
                rel="noopener" 
                target="_blank" 
                title="https://open.spotify.com/artist/22YNlwtEnx7AAsoZoZzmyF"
                href="https://open.spotify.com/artist/22YNlwtEnx7AAsoZoZzmyF">
                <svg 
                  xmlns="http://www.w3.org/2000/svg" 
                  width="25" 
                  height="25" 
                  class="spotify-svg" 
                  viewBox="0 0 16 16"> 
                  <path 
                    d="M8 0a8 8 0 1 0 0 16A8 8 0 0 0 8 0zm3.669 11.538a.498.498 0 0 1-.686.165c-1.879-1.147-4.243-1.407-7.028-.77a.499.499 0 0 1-.222-.973c3.048-.696 5.662-.397 7.77.892a.5.5 0 0 1 .166.686zm.979-2.178a.624.624 0 0 1-.858.205c-2.15-1.321-5.428-1.704-7.972-.932a.625.625 0 0 1-.362-1.194c2.905-.881 6.517-.454 8.986 1.063a.624.624 0 0 1 .206.858zm.084-2.268C10.154 5.56 5.9 5.419 3.438 6.166a.748.748 0 1 1-.434-1.432c2.825-.857 7.523-.692 10.492 1.07a.747.747 0 1 1-.764 1.288z"/> 
                </svg>
              </a>
            </li> -->
            <!-- <li class="amazon">
              <a 
                class="icon amazon" 
                rel="noopener" 
                target="_blank" 
                title="https://music.amazon.com/artists/B09DX5Z4LH/sheriff-crandy"
                href="https://music.amazon.com/artists/B09DX5Z4LH/sheriff-crandy">
                <svg 
                  xmlns="http://www.w3.org/2000/svg" 
                  width="50" 
                  height="20"
                  viewBox="0 0 112 65"
                  class="amazon-svg">
                  <path 
                    d="M72.37 27.38C65.59 32.35 55.77 35 47.3 35A45.5 45.5 0 0 1 16.7 23.38c-.64-.57-.07-1.35.69-.9a61.88 61.88 0 0 0 30.64 8.08c7.5 0 15.77-1.55 23.36-4.76 1.15-.48 2.11.75.99 1.58zm2.82-3.2c-.87-1.1-5.73-.53-7.91-.27-.67.08-.77-.5-.17-.91 3.88-2.71 10.23-1.93 10.97-1.02.75.91-.2 7.25-3.83 10.28-.56.47-1.09.22-.84-.4.82-2.03 2.65-6.58 1.78-7.68zM67.43 3.85V1.22c0-.4.3-.67.67-.67h11.87c.38 0 .68.27.68.66v2.26c0 .38-.32.88-.9 1.66l-6.14 8.73c2.28-.05 4.7.29 6.77 1.45.47.26.6.65.63 1.03v2.8c0 .4-.43.84-.87.6a13.73 13.73 0 0 0-12.54.03c-.42.22-.85-.22-.85-.61v-2.67c0-.43.01-1.16.44-1.81L74.32 4.5h-6.2c-.38 0-.69-.26-.7-.66zM90.87.21c5.36 0 8.26 4.58 8.26 10.4 0 5.62-3.2 10.08-8.26 10.08-5.26 0-8.12-4.58-8.12-10.28 0-5.74 2.9-10.2 8.12-10.2zm.03 3.76c-2.66 0-2.83 3.6-2.83 5.86 0 2.25-.03 7.06 2.8 7.06 2.8 0 2.93-3.88 2.93-6.25 0-1.55-.07-3.41-.54-4.88-.4-1.28-1.21-1.79-2.36-1.79zM61.61 20.26c-.24.2-.68.22-.85.08-1.24-.95-2.07-2.4-2.07-2.4-1.98 2.01-3.39 2.62-5.96 2.62-3.03 0-5.4-1.87-5.4-5.6a6.1 6.1 0 0 1 3.85-5.87c1.96-.86 4.7-1.01 6.79-1.25 0 0 .17-2.25-.44-3.07a2.54 2.54 0 0 0-2.03-.93c-1.33 0-2.63.72-2.89 2.11-.07.4-.36.74-.68.7l-3.45-.37a.63.63 0 0 1-.54-.75c.8-4.22 4.63-5.5 8.07-5.5 1.76 0 4.05.47 5.44 1.79 1.75 1.63 1.59 3.8 1.59 6.18v5.6c0 1.68.7 2.42 1.36 3.32.23.33.28.72-.01.96-.74.61-2.78 2.38-2.78 2.38zm-3.64-8.76v-.78c-2.61 0-5.37.56-5.37 3.62 0 1.55.81 2.6 2.2 2.6 1 0 1.92-.62 2.5-1.63.7-1.25.67-2.41.67-3.81zm-43.7 8.76c-.23.2-.67.22-.84.08-1.24-.95-2.07-2.4-2.07-2.4-1.99 2.01-3.39 2.62-5.96 2.62-3.04 0-5.4-1.87-5.4-5.6a6.1 6.1 0 0 1 3.85-5.87c1.96-.86 4.7-1.01 6.79-1.25 0 0 .17-2.25-.44-3.07a2.54 2.54 0 0 0-2.03-.93c-1.34 0-2.63.72-2.89 2.11-.07.4-.37.74-.68.7l-3.46-.37a.63.63 0 0 1-.53-.75C1.4 1.31 5.24.03 8.68.03c1.76 0 4.05.47 5.44 1.79C15.87 3.45 15.7 5.62 15.7 8v5.6c0 1.68.7 2.42 1.36 3.32.23.33.28.72-.01.96-.74.61-2.78 2.38-2.78 2.38zm-3.63-8.76v-.78c-2.61 0-5.37.56-5.37 3.62 0 1.55.8 2.6 2.2 2.6 1 0 1.92-.62 2.5-1.63.7-1.25.67-2.41.67-3.81zm14.2-1.63v9.76c0 .37-.3.67-.68.67h-3.6a.67.67 0 0 1-.68-.67V1.27c0-.37.3-.67.68-.67h3.37c.37 0 .67.3.67.67v2.35h.07C25.55 1.3 27.2.21 29.42.21c2.26 0 3.67 1.09 4.69 3.41A5.13 5.13 0 0 1 39.09.21c1.52 0 3.17.62 4.18 2.02 1.15 1.55.91 3.8.91 5.78v11.63c0 .37-.31.66-.7.66h-3.6a.67.67 0 0 1-.65-.66V9.87c0-.78.07-2.72-.1-3.45-.27-1.25-1.08-1.6-2.13-1.6a2.4 2.4 0 0 0-2.15 1.52c-.37.93-.34 2.48-.34 3.53v9.77c0 .37-.31.66-.7.66h-3.6a.67.67 0 0 1-.65-.66V9.87c0-2.06.33-5.08-2.23-5.08-2.6 0-2.5 2.94-2.5 5.08zm81.94 9.76c0 .37-.3.67-.67.67h-3.61a.67.67 0 0 1-.67-.67V1.27c0-.37.3-.67.67-.67h3.33c.4 0 .68.31.68.52v2.81h.07c1-2.52 2.42-3.72 4.92-3.72 1.62 0 3.2.58 4.21 2.17.94 1.48.94 3.96.94 5.74v11.6a.68.68 0 0 1-.69.58h-3.62a.68.68 0 0 1-.64-.58V8.58c0-3.72-1.43-3.83-2.26-3.83-.96 0-1.74.75-2.07 1.44a8.3 8.3 0 0 0-.6 3.52l.01 9.92zM.93 79.3c-.62 0-.93-.3-.93-.93V56.68c0-.62.31-.93.93-.93H3c.3 0 .55.07.72.19.17.12.29.36.35.7l.28 1.48c2.99-2.04 5.9-3.06 8.73-3.06 2.9 0 4.86 1.1 5.89 3.3 3.08-2.2 6.16-3.3 9.24-3.3 2.15 0 3.8.6 4.95 1.8 1.15 1.22 1.73 2.94 1.73 5.16v16.35c0 .62-.32.93-.94.93H31.2c-.62 0-.94-.3-.94-.93V63.33c0-1.55-.3-2.7-.88-3.44-.6-.75-1.53-1.12-2.8-1.12-2.28 0-4.56.7-6.87 2.1.03.21.05.44.05.69v16.81c0 .62-.31.93-.93.93h-2.76c-.62 0-.93-.3-.93-.93V63.33c0-1.55-.3-2.7-.89-3.44-.6-.75-1.53-1.12-2.8-1.12-2.37 0-4.64.68-6.82 2.05v17.55c0 .62-.3.93-.93.93H.93zm47.44.7c-2.21 0-3.9-.62-5.09-1.86-1.18-1.24-1.77-2.99-1.77-5.25V56.7c0-.63.3-.94.93-.94h2.75c.63 0 .94.31.94.93v14.73c0 1.67.32 2.9.98 3.69.65.79 1.7 1.18 3.13 1.18 2.24 0 4.5-.74 6.77-2.23V56.68c0-.62.3-.93.93-.93h2.75c.63 0 .94.31.94.93v21.7c0 .61-.31.92-.94.92h-2c-.31 0-.56-.06-.73-.18-.17-.13-.28-.36-.35-.7l-.32-1.62c-2.9 2.13-5.87 3.2-8.92 3.2zm26.52 0c-2.62 0-4.97-.43-7.05-1.3a1.83 1.83 0 0 1-.77-.51c-.14-.19-.21-.48-.21-.88V76c0-.56.18-.84.56-.84.22 0 .6.1 1.16.28 2.06.65 4.2.97 6.4.97 1.53 0 2.69-.3 3.48-.88.8-.59 1.19-1.44 1.19-2.55a2.4 2.4 0 0 0-.72-1.82 7.83 7.83 0 0 0-2.64-1.39l-3.97-1.48c-3.46-1.27-5.18-3.44-5.18-6.5 0-2.02.78-3.65 2.36-4.88 1.57-1.24 3.63-1.86 6.18-1.86a17 17 0 0 1 5.93 1.07c.37.12.64.28.8.48.15.2.23.5.23.9v1.26c0 .56-.2.84-.6.84a4.2 4.2 0 0 1-1.08-.23c-1.65-.5-3.33-.75-5.05-.75-2.98 0-4.48 1.01-4.48 3.02 0 .8.25 1.44.75 1.9.5.47 1.48.98 2.94 1.54l3.64 1.4c1.84.7 3.16 1.55 3.97 2.53.81.97 1.21 2.23 1.21 3.78 0 2.2-.82 3.95-2.47 5.25-1.65 1.3-3.84 1.95-6.58 1.95zm14.94-.7c-.62 0-.94-.3-.94-.93V56.68c0-.62.32-.93.94-.93h2.75c.62 0 .94.31.94.93v21.7c0 .61-.32.92-.94.92h-2.75zm1.4-27.73c-.9 0-1.61-.25-2.13-.76a2.72 2.72 0 0 1-.77-2.02c0-.84.26-1.51.77-2.02a2.88 2.88 0 0 1 2.13-.77c.9 0 1.6.26 2.12.77.52.5.77 1.18.77 2.02 0 .83-.25 1.5-.77 2.02-.51.5-1.22.76-2.12.76zm19.51 28.24c-3.67 0-6.48-1.04-8.42-3.13-1.95-2.1-2.92-5.12-2.92-9.08 0-3.93 1-6.98 3.01-9.13 2-2.15 4.85-3.23 8.52-3.23 1.68 0 3.33.3 4.95.89.34.12.58.27.72.46s.21.5.21.93v1.25c0 .62-.2.93-.6.93-.16 0-.4-.04-.75-.14a13.8 13.8 0 0 0-3.88-.55c-2.61 0-4.5.65-5.65 1.97-1.15 1.32-1.72 3.41-1.72 6.3v.6c0 2.81.58 4.88 1.75 6.2 1.17 1.31 3.01 1.97 5.53 1.97 1.3 0 2.7-.21 4.2-.65.35-.1.58-.14.7-.14.4 0 .61.31.61.93v1.26c0 .4-.06.7-.19.88-.12.18-.37.35-.74.5-1.53.66-3.3.98-5.33.98z"/>
                </svg>
              </a>
            </li> -->
            <li class="instagram">
                <a 
                  class="icon instagram" 
                  rel="noopener" 
                  target="_blank" 
                  title="https://www.instagram.com/sheriffcrandy/"
                  href="#">
                  <svg
                    xmlns="http://www.w3.org/2000/svg" 
                    viewBox="0 0 18 18" 
                    class="icon">
                    <path 
                      fill-rule="evenodd" 
                      d="M6.955 1.628l2.582-.006c1.916.001 2.227.012 3.1.052.877.04 1.354.187 1.67.31.421.163.72.358 1.036.673.27.27.452.529.6.862l.073.173c.113.29.246.715.298 1.46l.03.627c.012.29.02.553.025.917l.01 2.842c-.002 1.915-.013 2.226-.053 3.099-.037.804-.163 1.272-.279 1.588l-.031.083c-.163.42-.358.72-.673 1.035-.315.315-.615.51-1.035.673-.29.113-.715.246-1.46.298l-1.21.05c-.344.007-.761.011-1.428.013l-3.255-.005a37.01 37.01 0 01-1.592-.046c-.877-.04-1.354-.187-1.67-.31a2.788 2.788 0 01-1.036-.673 2.788 2.788 0 01-.673-1.035c-.113-.29-.246-.715-.298-1.46l-.05-1.21a71.292 71.292 0 01-.013-1.428l.005-3.255c.006-.692.02-1.022.046-1.592.04-.877.187-1.354.31-1.67.163-.421.358-.72.673-1.036.315-.315.615-.51 1.035-.673.29-.113.715-.246 1.46-.298l.627-.03c.355-.015.668-.023 1.176-.028zM6.97.006h4.06c.747.007 1.09.021 1.68.048.959.044 1.613.196 2.185.419.592.23 1.094.537 1.594 1.038.5.5.808 1.002 1.038 1.594.198.509.34 1.082.4 1.876l.035.68c.026.62.036 1.093.038 2.574l-.005 2.658c-.006.844-.02 1.192-.05 1.818-.043.958-.195 1.612-.418 2.184a4.412 4.412 0 01-1.038 1.594c-.5.5-1.002.809-1.594 1.039-.509.197-1.082.34-1.876.4l-.795.039c-.53.021-1.003.03-2.193.032l-2.924-.004a39.115 39.115 0 01-1.818-.05c-.958-.043-1.612-.195-2.184-.417a4.412 4.412 0 01-1.594-1.039c-.5-.5-.809-1.002-1.039-1.594-.197-.509-.34-1.082-.4-1.876l-.042-.876C.009 11.575 0 11.027 0 9.527L.006 6.97c.007-.747.021-1.09.048-1.68.044-.959.196-1.613.418-2.185A4.412 4.412 0 011.511 1.51c.5-.5 1.002-.808 1.594-1.038.509-.198 1.082-.34 1.876-.4L5.857.03C6.177.018 6.49.01 6.97.006zm2.048 4.387a4.625 4.625 0 100 9.25 4.625 4.625 0 000-9.25zm0 1.623a3.002 3.002 0 110 6.004 3.002 3.002 0 010-6.004zm4.768-2.909a1.071 1.071 0 100 2.143 1.071 1.071 0 000-2.143z">
                    </path>
                  </svg>
                </a>
            </li>
            <!-- <li class="youtube">
                <a 
                  class="icon youtube" 
                  rel="noopener" 
                  target="_blank" 
                  title="https://www.youtube.com/@sheriffcrandy"
                  href="https://www.youtube.com/@sheriffcrandy">
                  <svg 
                    xmlns="http://www.w3.org/2000/svg" 
                    viewBox="0 0 18 14" 
                    class="icon">
                    <path 
                      d="M7.518.011l1.81-.01c.971.004 3.89.03 5.972.173l.355.05c.394.061.95.209 1.445.76.463.478.66 1.426.714 1.746l.017.108s.155 1.378.168 2.816L18 7.241c0 .654-.032 1.31-.068 1.84l-.1 1.172s-.17 1.274-.732 1.853c-.675.753-1.463.753-1.8.811l-.537.033c-2.11.12-4.778.138-5.547.14l-2.132-.03c-1.465-.029-3.372-.076-4.215-.143-.394-.116-1.294-.058-1.969-.81-.43-.444-.63-1.293-.7-1.668l-.031-.186S.014 8.875 0 7.437V5.654l.007-.39c.012-.45.035-.883.06-1.254l.1-1.172S.339 1.564.9.985C1.575.232 2.362.232 2.7.174l.75-.045C4.827.057 6.4.025 7.518.01zm-.973 3.262v6.545l6.546-3.273-6.546-3.272z">
                    </path>
                  </svg>
                </a>
            </li> -->
            <li class="twitter">
                <a 
                  class="icon twitter" 
                  rel="noopener" 
                  target="_blank" 
                  title="https://twitter.com/sheriffcrandy"
                  href="#">
                  <!-- <svg 
                    xmlns="http://www.w3.org/2000/svg" 
                    viewBox="0 0 18 16" 
                    class="icon">
                    <path 
                      fill-rule="evenodd" 
                      d="M15.88 2.44A3.866 3.866 0 0017.502.284a7.162 7.162 0 01-2.345.945A3.595 3.595 0 0012.462 0C10.422 0 8.77 1.744 8.77 3.894c0 .306.03.603.094.887C5.796 4.62 3.076 3.07 1.253.712a4.05 4.05 0 00-.5 1.959c0 1.35.652 2.543 1.643 3.243a3.56 3.56 0 01-1.673-.487v.048c0 1.887 1.272 3.462 2.963 3.818-.31.092-.636.137-.974.137-.238 0-.47-.023-.694-.069.47 1.547 1.833 2.675 3.45 2.705A7.17 7.17 0 010 13.679a10.07 10.07 0 005.66 1.75c6.794 0 10.507-5.935 10.507-11.082 0-.17-.002-.338-.01-.504A7.72 7.72 0 0018 1.826c-.662.31-1.375.52-2.12.613z">
                    </path>
                  </svg> -->
                  <svg 
                    viewBox="0 0 1200 1227" 
                    xmlns="http://www.w3.org/2000/svg" 
                    aria-hidden="true" 
                    role="none" 
                    class="u01b__icon-home"> 
                    <path 
                      :class="$store.state.theme_change"
                      d="M714.163 519.284L1160.89 0H1055.03L667.137 450.887L357.328 0H0L468.492 681.821L0 1226.37H105.866L515.491 750.218L842.672 1226.37H1200L714.137 519.284H714.163ZM569.165 687.828L521.697 619.934L144.011 79.6944H306.615L611.412 515.685L658.88 583.579L1055.08 1150.3H892.476L569.165 687.854V687.828Z">
                    </path> 
                  </svg>
                </a>
            </li>
            <li class="gab">
                <a 
                  class="icon gab" 
                  rel="noopener" 
                  target="_blank" 
                  title="https://gab.com/LCTechnologies"
                  href="https://gab.com/LCTechnologies">
                  <!-- viewbox 
                  min-x (horizontal axis), 
                  min-y (vertical axis),
                  width
                  height 
                  -->

                  <svg 
                    class="gab-svg"
                    version="1.1" 
                    xmlns="http://www.w3.org/2000/svg" 
                    x="0px" 
                    y="0px" 
                    width="45" 
                    height="30" 
                    viewBox="0 0 50 35" 
                    xml:space="preserve"
                    >
                      <!-- g -->
                      <path 
                        d="M13.8,7.6h-2.4v0.7V9l-0.4-0.3C10.2,7.8,9,7.2,7.7,7.2c-0.2,0-0.4,0-0.4,0c-0.1,0-0.3,0-0.5,0
                          c-5.6,0.3-8.7,7.2-5.4,12.1c2.3,3.4,7.1,4.1,9.7,1.5l0.3-0.3l0,0.7c0,1-0.1,1.5-0.4,2.2c-1,2.4-4.1,3-6.8,1.3
                          c-0.2-0.1-0.4-0.2-0.4-0.2c-0.1,0.1-1.9,3.5-1.9,3.6c0,0.1,0.5,0.4,0.8,0.6c2.2,1.4,5.6,1.7,8.3,0.8c2.7-0.9,4.5-3.2,5-6.4
                          c0.2-1.1,0.2-0.8,0.2-8.4l0-7.1H13.8z M9.7,17.6c-2.2,1.2-4.9-0.4-4.9-2.9C4.8,12.6,7,11,9,11.6C11.8,12.4,12.3,16.1,9.7,17.6z">
                      </path>
                      <!-- b -->
                      <path 
                        d="M45.6,7.7c-2.4-1-5-0.6-6.7,1L38.6,9V4.5V0h-2.4h-2.4v11v11h2.4h2.4v-0.7v-0.7l0.3,0.3
                          c2.4,2.4,6.9,1.9,9.3-0.9C51.5,15.9,50.1,9.6,45.6,7.7z M43.7,17.5c-2.1,1.4-5.1-0.2-5.1-2.8c0-2.1,1.9-3.7,3.9-3.3
                          C45.4,12.1,46.2,15.8,43.7,17.5z">
                      </path>
                      <!-- a -->
                      <path 
                        d="M31.5,12.5c-0.7-3.7-3.1-5.5-7.1-5.3c-1.7,0.1-4,0.7-4.8,1.4l-0.1,0.1l0.7,1.7c0.4,0.9,0.7,1.7,0.7,1.7
                          c0,0,0.1,0,0.2-0.1c2.7-1.4,5.4-0.9,5.6,1.1l0,0.2l-0.4-0.1c-3-0.8-6.3-0.1-7.7,1.6c-1.8,2.2-0.9,5.8,1.7,7.1
                          c2.1,1,4.6,0.6,6.1-0.8l0.2-0.2v0.6v0.6h2.4h2.4v-4C31.7,13.7,31.7,13.3,31.5,12.5z M26.9,16.4c-0.1,0.7-0.5,1.5-1,2
                          c-1.2,1.1-3,0.7-3.2-0.7c-0.2-1,0.6-1.7,2-1.8c0.1,0,0.2,0,0.2,0c0,0,0.2,0,0.4,0c0.5,0,1,0.1,1.4,0.2l0.3,0.1L26.9,16.4z">
                      </path>
                  </svg>
                </a>
            </li>
          </ul>
        </div>          
        <!-- lctec brand-->
        <div class="lctec-brand">
          Jesus Christ is Lord
          <p class="company_link">
            &copy; 2022-2024 | 
            LC Technologies 
            <img alt="lctec_icon" class="lctec-icon" type="image/png" src="../src/assets/images/lctec_icon_rounded.png">
          </p>
            <!-- <a class="company_link"
                href="https://lctechnologies.azurewebsites.net/" target="_blank">
              LC Technologies
              <img alt="lctec_icon" class="lctec-icon" type="image/png" src="../src/assets/images/lctec_icon_rounded.png">
            </a> 				 
            Linden Crandall -->
        </div>           
      </footer>
      <div v-if="showScrollArrow" class="scroll-top-btn-container">
        <span class="my-scroll-up-btn-span" @click="scrollToTop()">
            <i class="fas fa-solid fa-arrow-up my-scroll-up-btn-arrow"></i>
        </span>
    </div>          
</template>

<style lang="scss">
@import '../node_modules/bulma';
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>

<!-- import required css files -->
<style>
  @import '../src/assets/styles/my-nav.css';
  @import '../src/assets/styles/my-locale-dropdown.css';
  @import '../src/assets/styles/my-footer.css';
  @import '../src/assets/styles/my-contact.css';
  @import '../src/assets/styles/my-style.css';
  @import '../src/assets/styles/my-theme-toggle.css';
  @import '../src/assets/styles/my-theme.css';
  @import '../src/assets/styles/my-landing.css';
  @import '../src/assets/styles/my-services.css';
</style>


<script>

// import axios for retrieving web token from backend api
import axios from 'axios'
import HomeView from '@/views/HomeView.vue';

// change hamburger clicked boolean
export default {

  data () {
    return {
      hamburgerClicked: false,
      showScrollArrow: false,
      windowTop: 0,
      userCountry: null,
      userIP: null
    }
  },

  // initialize the store. First method that is called when app is loaded/page refreshed
  beforeCreate() {

  },

  created() {
      window.addEventListener('scroll', this.handleScroll, true);     

  },

  destroyed() {
      window.removeEventListener('scroll', this.handleScroll, true);     

  },  

  components: {
    HomeView,
  },


  mounted() {

    if (!this.userCountry || !this.userIP) {
      // set locale and region
      // get the ip address
      this.getuserCountryByIP()
    }

    if (localStorage.getItem('theme') == 'lightTheme') {

        this.$store.commit('setTheme', 'lightTheme')
    }
    else {
      this.$store.commit('setTheme', 'darkTheme')

    }


    // dropdown show and hide on hover for services
    document.addEventListener("mouseover", e => {
      let isDropdownButton = null
      let dropdown = null
      try {
        isDropdownButton = e.target.matches("[data-dropdown-button-services]");
        dropdown = e.target.closest("[data-dropdown-services]");
      }
      catch {
        return
      }

      if (!dropdown) return;

      if (isDropdownButton || dropdown.querySelector(":hover")) {
        dropdown.classList.add("active");
      }
    });

    document.addEventListener("mouseout", e => {

      let dropdown = null

      try {
        dropdown = e.target.closest("[data-dropdown-services]");
      }
      catch {
        return
      }

      if (!dropdown) return;

      // Check if the mouse is not over the dropdown or the dropdown button
      if (!dropdown.contains(e.relatedTarget) && 
          !e.relatedTarget.matches("[data-dropdown-button-services]") && 
          !dropdown.querySelector(":hover")) {
        dropdown.classList.remove("active");
      }
    });    


    // dropdown show and hide on hover for locale
    document.addEventListener("mouseover", e => {

      let isDropdownButton = null
      let dropdown = null

      try {
        isDropdownButton = e.target.matches("[data-dropdown-button]");
        dropdown = e.target.closest("[data-dropdown]");
      }
      catch {
        return
      }

      if (!dropdown) return;

      if (isDropdownButton || dropdown.querySelector(":hover")) {
        dropdown.classList.add("active");
      }
    });

    document.addEventListener("mouseout", e => {

      let dropdown = null;

      try {
        dropdown = e.target.closest("[data-dropdown]");
      }
      catch {
        return
      }

      if (!dropdown) return;

      // Check if the mouse is not over the dropdown or the dropdown button
      if (!dropdown.contains(e.relatedTarget) && 
          !e.relatedTarget.matches("[data-dropdown-button]") && 
          !dropdown.querySelector(":hover")) {
        dropdown.classList.remove("active");
      }
    });

  },
  computed: {

  },

  // methods 
  methods: {

    getuserCountryByIP() {

      axios.get(process.env.VUE_APP_GET_USER_IP, 
      {
          headers: 
          { 
          'api-key': process.env.VUE_APP_API_KEY
          } 
      }).then(response => {

          if (response.data.none == "none") {
            this.userCountry = (this.$t('locationNotAvailable'))
            this.userIP = (this.$t('ipNotAvailable'))
          }
          else {
            this.userIP = response.data.ip;
            this.userCountry = response.data.city_name + ", " + response.data.region_name + ", " + response.data.country_name;
          }

        })
        .catch(error => {

        this.userCountry = (this.$t('locationNotAvailable'))
        this.userIP = (this.$t('ipNotAvailable'))

    }); 
    },

    handleScroll(e) {
        this.windowTop = e.target.scrollTop;
        this.showScrollArrow = this.windowTop > 140;
    },
    scrollToTop() {
        document.body.scrollTo({ top: 0, behavior: 'smooth' })
    },       

    closeNav: function() {
      current_width = window.innerWidth;

      if (current_width > 1024) {
        return {
          myWidth: "100"
        }
      }
      else {
        return {
          myWidth: "0"
        }
      }
    },

    scrollTo(section) {
      this.$store.commit('scrollTo', section)
    },
    // toggle theme
    toggleTheme() {
      this.$store.commit('toggleTheme')
    },

    // change region button click
    changeRegionButton(region) {
      this.$store.commit('setRegion',region)
      window.location.reload();
    },
    // change language button click
    changeLanguageButton(language) {
      this.$store.commit('setLanguage',language)
      window.location.reload();
    },
  }
}
</script> 