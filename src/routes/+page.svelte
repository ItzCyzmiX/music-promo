<script>
  import { onMount } from 'svelte';
    import { fly, scale } from 'svelte/transition';
  
  // State using Svelte 5 runes
  let selectedAlbum = $state(null);
  let showMobileMenu = $state(false);

  let loaded = $state(false);

  
  // Sample album data
  const albums = {
    'midnight-echoes': {
      id: 'midnight-echoes',
      title: 'Midnight Echoes',
      year: '2024',
      type: 'Album',
      trackCount: 10,
      duration: '42 min',
      tracks: [
        { number: 1, title: 'Intro (Midnight)', duration: '2:15' },
        { number: 2, title: 'Echoes in the Dark', duration: '4:32' },
        { number: 3, title: 'Neon Lights', duration: '3:45' },
        { number: 4, title: 'City Sleep', duration: '5:12' },
        { number: 5, title: 'Digital Dreams', duration: '4:18' },
        { number: 6, title: 'Midnight Train', duration: '3:56' },
        { number: 7, title: 'Lost in Translation', duration: '4:42' },
        { number: 8, title: 'Binary Hearts', duration: '3:28' },
        { number: 9, title: 'Outro (Dawn)', duration: '2:55' },
        { number: 10, title: 'Echoes (Reprise)', duration: '6:34' }
      ]
    },
    'neon-dreams': {
      id: 'neon-dreams',
      title: 'Neon Dreams',
      year: '2023',
      type: 'Album',
      trackCount: 8,
      duration: '35 min',
      tracks: [
        { number: 1, title: 'Electric Pulse', duration: '4:12' },
        { number: 2, title: 'Neon Dreams', duration: '3:47' },
        { number: 3, title: 'Synthetic Love', duration: '4:33' },
        { number: 4, title: 'Circuit Board', duration: '3:21' },
        { number: 5, title: 'Digital Horizon', duration: '5:15' },
        { number: 6, title: 'Cyber Romance', duration: '4:01' },
        { number: 7, title: 'Matrix Rain', duration: '3:38' },
        { number: 8, title: 'Neon Nights', duration: '6:22' }
      ]
    },
    'urban-symphony': {
      id: 'urban-symphony',
      title: 'Urban Symphony',
      year: '2022',
      type: 'EP',
      trackCount: 5,
      duration: '22 min',
      tracks: [
        { number: 1, title: 'Urban Jungle', duration: '4:45' },
        { number: 2, title: 'Street Lights', duration: '3:52' },
        { number: 3, title: 'Metropolitan', duration: '4:18' },
        { number: 4, title: 'City Rhythm', duration: '3:34' },
        { number: 5, title: 'Concrete Dreams', duration: '5:28' }
      ]
    },
    'midnight-dechoes': {
      id: 'midnight-echoes',
      title: 'Midnight Echoes',
      year: '2024',
      type: 'Album',
      trackCount: 10,
      duration: '42 min',
      tracks: [
        { number: 1, title: 'Intro (Midnight)', duration: '2:15' },
        { number: 2, title: 'Echoes in the Dark', duration: '4:32' },
        { number: 3, title: 'Neon Lights', duration: '3:45' },
        { number: 4, title: 'City Sleep', duration: '5:12' },
        { number: 5, title: 'Digital Dreams', duration: '4:18' },
        { number: 6, title: 'Midnight Train', duration: '3:56' },
        { number: 7, title: 'Lost in Translation', duration: '4:42' },
        { number: 8, title: 'Binary Hearts', duration: '3:28' },
        { number: 9, title: 'Outro (Dawn)', duration: '2:55' },
        { number: 10, title: 'Echoes (Reprise)', duration: '6:34' }
      ]
    },
    'neon-dredams': {
      id: 'neon-dreams',
      title: 'Neon Dreams',
      year: '2023',
      type: 'Album',
      trackCount: 8,
      duration: '35 min',
      tracks: [
        { number: 1, title: 'Electric Pulse', duration: '4:12' },
        { number: 2, title: 'Neon Dreams', duration: '3:47' },
        { number: 3, title: 'Synthetic Love', duration: '4:33' },
        { number: 4, title: 'Circuit Board', duration: '3:21' },
        { number: 5, title: 'Digital Horizon', duration: '5:15' },
        { number: 6, title: 'Cyber Romance', duration: '4:01' },
        { number: 7, title: 'Matrix Rain', duration: '3:38' },
        { number: 8, title: 'Neon Nights', duration: '6:22' }
      ]
    },
    'urban-sddymphony': {
      id: 'urban-symphony',
      title: 'Urban Symphony',
      year: '2022',
      type: 'EP',
      trackCount: 5,
      duration: '22 min',
      tracks: [
        { number: 1, title: 'Urban Jungle', duration: '4:45' },
        { number: 2, title: 'Street Lights', duration: '3:52' },
        { number: 3, title: 'Metropolitan', duration: '4:18' },
        { number: 4, title: 'City Rhythm', duration: '3:34' },
        { number: 5, title: 'Concrete Dreams', duration: '5:28' }
      ]
    }
  };

  function showAlbum(albumId) {
    selectedAlbum = albums[albumId];
  }

  function hideAlbum() {
    selectedAlbum = null;
  }

  function smoothScroll(elementId) {
    document.getElementById(elementId)?.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    });
  }

  onMount( async() => {
    loaded = true;
  });
</script>

<main class="bg-vercel-bg text-vercel-text min-h-screen">
  <!-- Navigation -->
  <nav class="border-b border-vercel-border sticky top-0 bg-vercel-bg/95 backdrop-blur-md z-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <div class="flex items-center space-x-8">
          <div class="text-xl font-bold text-vercel-accent">CyzmiX</div>
          <div class="hidden md:flex space-x-6">
            <button onclick={() => smoothScroll('home')} class="nav-link text-vercel-muted hover:text-vercel-accent cursor-pointer">Home</button>
            <button onclick={() => smoothScroll('music')} class="nav-link text-vercel-muted hover:text-vercel-accent cursor-pointer">Music</button>
            <button onclick={() => smoothScroll('about')} class="nav-link text-vercel-muted hover:text-vercel-accent cursor-pointer">About</button>
            <button onclick={() => smoothScroll('contact')} class="nav-link text-vercel-muted hover:text-vercel-accent cursor-pointer">Contact</button>
          </div>
        </div>
        <div class="flex items-center space-x-4">
          <a href="https://open.spotify.com/intl-fr/artist/5R9XKpQxEuF7moLOM4VloK" target="_blank" class="hidden md:block bg-vercel-accent text-vercel-bg px-4 py-2 rounded-lg hover:bg-white/10 transition-colors">
            Listen Now
          </a>
          <button 
            class="md:hidden text-vercel-muted"
            onclick={() => showMobileMenu = !showMobileMenu}
          >
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </nav>

  <!-- Mobile Menu -->
  {#if showMobileMenu}
    <div class="md:hidden bg-vercel-card border-b border-vercel-border">
      <div class="px-4 py-4 space-y-2">
        <button onclick={() => {smoothScroll('home'); showMobileMenu = false;}} class="block w-full text-left py-2 text-vercel-muted hover:text-vercel-accent">Home</button>
        <button onclick={() => {smoothScroll('music'); showMobileMenu = false;}} class="block w-full text-left py-2 text-vercel-muted hover:text-vercel-accent">Music</button>
        <button onclick={() => {smoothScroll('about'); showMobileMenu = false;}} class="block w-full text-left py-2 text-vercel-muted hover:text-vercel-accent">About</button>
        <button onclick={() => {smoothScroll('contact'); showMobileMenu = false;}} class="block w-full text-left py-2 text-vercel-muted hover:text-vercel-accent">Contact</button>
      </div>
    </div>
  {/if}
    {#if loaded}
  <!-- Hero Section -->
  <section id="home" class="hero-gradient relative py-20 md:py-32 overflow-hidden" >
    <!-- Grid Background -->
    <div class="absolute inset-0 grid-background"></div>
    
    <!-- Content with z-index to appear above grid -->
    <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center" transition:fly={{ y: 50, duration: 500 }}>
      <h1 class="text-4xl md:text-6xl font-bold mb-6 text-vercel-accent">
        Hello!
      </h1>
      <p class="text-xl md:text-2xl text-vercel-muted mb-8 max-w-3xl mx-auto">
        Welcome to my musical heaven, it's not as good as it sounds
      </p>

    </div>
  </section>
  {/if}
  <!-- Music Section -->
  <section id="music" class="py-20">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="mb-12">
        <h2 class="text-3xl md:text-4xl font-bold mb-4 text-vercel-accent">Discography (the lack thereof)</h2>
      
      </div>

      {#if !selectedAlbum }
        <!-- Albums Grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          {#each Object.values(albums) as album, id}
          {#if loaded}
            <div class="album-card cursor-pointer" onclick={() => showAlbum(album.id)} transition:fly={{ y: 50, duration: 500, delay: id * 100 }}>
              <div class="album-cover bg-vercel-card rounded-lg mb-4 flex items-center justify-center aspect-square hover:scale-103 hover:shadow-2xl transition-all duration-300">
                <svg class="w-16 h-16 text-vercel-muted" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 19V6l12-3v13M9 19c0 1.105-1.343 2-3 2s-3-.895-3-2 1.343-2 3-2 3 .895 3 2zm12-3c0 1.105-1.343 2-3 2s-3-.895-3-2 1.343-2 3-2 3 .895 3 2zM9 10l12-3"></path>
                </svg>
              </div>
              <h3 class="text-xl font-bold mb-2 text-vercel-accent">{album.title}</h3>
              <p class="text-vercel-muted mb-2">{album.year} • {album.type}</p>
              <p class="text-sm text-vercel-muted">{album.trackCount} tracks • {album.duration}</p>
            </div>
            {/if}
          {/each}
        </div>
      {:else}
        <!-- Album Detail View -->
        <div class="album-detail" transition:fly={{ y: -50, duration: 300 }}>

          <div class="flex flex-col md:flex-row gap-8 mb-8" >
            
            <div class="md:w-80">
                                              <button onclick={hideAlbum} class="text-vercel-muted hover:text-vercel-accent mb-8 flex items-center gap-2 cursor-pointer">
                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path>
                </svg>
                Back to Albums
              </button>
              <div class="album-cover bg-vercel-card rounded-lg flex items-center justify-center mb-4 aspect-square">
                <svg class="w-24 h-24 text-vercel-muted" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 19V6l12-3v13M9 19c0 1.105-1.343 2-3 2s-3-.895-3-2 1.343-2 3-2 3 .895 3 2zm12-3c0 1.105-1.343 2-3 2s-3-.895-3-2 1.343-2 3-2 3 .895 3 2zM9 10l12-3"></path>
                </svg>
              </div>

            </div>
            <div class="flex-1">
              <p class="text-vercel-muted mb-2">{selectedAlbum.type.toUpperCase()}</p>
              <h2 class="text-4xl md:text-5xl font-bold mb-4 text-vercel-accent">{selectedAlbum.title}</h2>
              <p class="text-vercel-muted mb-6">Artist Name • {selectedAlbum.year} • {selectedAlbum.type} • {selectedAlbum.trackCount} tracks</p>
              <div class="flex items-center gap-4 mb-8">
                <button class="cursor-pointer bg-vercel-accent text-vercel-bg px-8 py-3 rounded-full font-semibold hover:bg-white/10 transition-colors flex items-center gap-2">
                  <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                    <path d="M8 5v14l11-7z"/>
                  </svg>
                  Play
                </button>
              </div>
            </div>
          </div>

          <!-- Track List -->
          <div class="bg-vercel-card rounded-lg p-6">
            <div class="grid grid-cols-12 gap-4 mb-4 text-vercel-muted text-sm font-medium border-b border-vercel-border pb-2">
              <div class="col-span-1">#</div>
              <div class="col-span-6">Title</div>
              <div class="col-span-3 hidden md:block">Album</div>
              <div class="col-span-2 text-right">Duration</div>
            </div>
            {#each selectedAlbum.tracks as track}
              <div class="track-row grid grid-cols-12 gap-4 py-3 px-2 rounded-lg cursor-pointer group hover:bg-white/5 transition-colors">
                <div class="col-span-1 flex items-center">
                  <span class="track-number text-vercel-muted group-hover:opacity-0 transition-opacity">{track.number}</span>
                  <button class="play-button w-6 h-6 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity absolute">
                    <svg class="w-4 h-4 text-vercel-accent" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M8 5v14l11-7z"/>
                    </svg>
                  </button>
                </div>
                <div class="col-span-6 flex items-center">
                  <span class="text-vercel-accent font-medium">{track.title}</span>
                </div>
                <div class="col-span-3 hidden md:flex items-center">
                  <span class="text-vercel-muted">{selectedAlbum.title}</span>
                </div>
                <div class="col-span-2 flex items-center justify-end">
                  <span class="text-vercel-muted">{track.duration}</span>
                </div>
              </div>
            {/each}
          </div>
        </div>
      {/if}
    </div>
  </section>

  <!-- About Section -->
  <section id="about" class="py-20 bg-vercel-card">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="max-w-3xl mx-auto text-center">
        <h2 class="text-3xl md:text-4xl font-bold mb-6 text-vercel-accent">About my ass music</h2>
        <p class="text-lg text-vercel-muted mb-8">
          i make music cuz im bored, and apparentlly 14 ppl listen to it, crazy
        </p>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div class="text-center">
            <div class="text-2xl font-bold text-vercel-accent mb-2">13+</div>
            <div class="text-vercel-muted">Monthly Listeners</div>
          </div>
          <div class="text-center">
            <div class="text-2xl font-bold text-vercel-accent mb-2">12</div>
            <div class="text-vercel-muted">Albums Released</div>
          </div>
          <div class="text-center">
            <div class="text-2xl font-bold text-vercel-accent mb-2">23</div>
            <div class="text-vercel-muted">Total Tracks</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Contact Section -->
  <!-- <section id="contact" class="py-20">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="max-w-2xl mx-auto text-center">
        <h2 class="text-3xl md:text-4xl font-bold mb-6 text-vercel-accent">Get in Touch</h2>
        <p class="text-lg text-vercel-muted mb-8">
          if u wanna collab, or just to say hello.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <a href="mailto:contact@artist.com" class="bg-vercel-accent text-vercel-bg px-8 py-3 rounded-lg font-semibold hover:bg-gray-200 transition-colors">
            Email Me
          </a>
          <a href="#" class="border border-vercel-border px-8 py-3 rounded-lg font-semibold hover:bg-vercel-card transition-colors">
            Social Media
          </a>
        </div>
      </div>
    </div>
  </section> -->

  <!-- Footer -->
  <footer class="border-t border-vercel-border py-12">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center text-vercel-muted">
        <p>&copy; 2025 CyzmiX. All rights reserved.</p>
      </div>
    </div>
  </footer>
</main>

<style>
  :global(body) {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', sans-serif;
    background-color: #0a0a0a;
    color: #ededed;
  }

  :global(.bg-vercel-bg) { background-color: #0a0a0a; }
  :global(.bg-vercel-card) { background-color: #111111; }
  :global(.border-vercel-border) { border-color: #333333; }
  :global(.text-vercel-text) { color: #ededed; }
  :global(.text-vercel-muted) { color: #888888; }
  :global(.text-vercel-accent) { color: #ffffff; }

  .grid-background {
    background-image: linear-gradient(rgba(255, 255, 255, 0.05) 1px, transparent 1px),
                      linear-gradient(to right, rgba(255, 255, 255, 0.05) 1px, transparent 1px);
    background-size: 50px 50px;
    mask-image: linear-gradient(to bottom, transparent, 15%, white, 85%, transparent);
    animation: drift 60s linear infinite;
  }

  @keyframes drift {
    from {
      transform: translate(0);
    }
    to {
      transform: translate(-50px, -50px);
    }
  }

  .hero-gradient {
    background: linear-gradient(135deg, #111111 0%, #0a0a0a 100%);
  }

  .nav-link {
    transition: color 0.3s ease;
  }

  .album-cover {
    aspect-ratio: 1;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  .album-cover:hover {
    transform: scale(1.05);
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
  }

  .track-row:hover {
    background-color: rgba(255, 255, 255, 0.05);
  }

  .play-button {
    transition: opacity 0.3s ease;
  }

  .track-number {
    transition: opacity 0.3s ease;
  }
</style>