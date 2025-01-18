+++
date = '2025-01-17T16:17:40+03:30'
draft = false
title = 'First Post'
+++

<audio controls>
  <source src="/audio/Scrum.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>

## Welcome to My First Post!

{{< rawhtml >}}
<img src="/images/scrum.jpg" alt="Scrum book Picture" class="profile-picture">
{{< /rawhtml >}}

This is the content of my first blog post. I’m excited to share my thoughts and ideas with you. 

You can listen to the audio version of this post using the player above. Enjoy!
[Download Audio](/audio/Scrum.mp3)

{{< rawhtml >}}
<div id="music-player">
  <audio id="audio" src="/audio/Scrum.mp3"></audio>
  <div class="controls">
    <button id="play-pause">Play</button>
    <input type="range" id="seek-bar" value="0">
    <span id="current-time">0:00</span> / <span id="duration">0:00</span>
    <button id="mute">Mute</button>
    <input type="range" id="volume-bar" min="0" max="1" step="0.1" value="1">
  </div>
</div>

<style>
  #music-player {
    max-width: 400px;
    margin: 20px auto;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 10px;
    background-color: #f9f9f9;
    text-align: center;
  }

  .controls {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  #seek-bar, #volume-bar {
    width: 100%;
  }

  button {
    padding: 5px 10px;
    border: none;
    border-radius: 5px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
  }

  button:hover {
    background-color: #0056b3;
  }
</style>

<script>
  const audio = document.getElementById('audio');
  const playPauseButton = document.getElementById('play-pause');
  const seekBar = document.getElementById('seek-bar');
  const currentTime = document.getElementById('current-time');
  const duration = document.getElementById('duration');
  const muteButton = document.getElementById('mute');
  const volumeBar = document.getElementById('volume-bar');

  // Play/Pause functionality
  playPauseButton.addEventListener('click', () => {
    if (audio.paused) {
      audio.play();
      playPauseButton.textContent = 'Pause';
    } else {
      audio.pause();
      playPauseButton.textContent = 'Play';
    }
  });

  // Update seek bar as the audio plays
  audio.addEventListener('timeupdate', () => {
    seekBar.value = audio.currentTime;
    currentTime.textContent = formatTime(audio.currentTime);
  });

  // Update duration when the audio metadata is loaded
  audio.addEventListener('loadedmetadata', () => {
    seekBar.max = audio.duration;
    duration.textContent = formatTime(audio.duration);
  });

  // Seek functionality
  seekBar.addEventListener('input', () => {
    audio.currentTime = seekBar.value;
  });

  // Mute functionality
  muteButton.addEventListener('click', () => {
    audio.muted = !audio.muted;
    muteButton.textContent = audio.muted ? 'Unmute' : 'Mute';
  });

  // Volume control
  volumeBar.addEventListener('input', () => {
    audio.volume = volumeBar.value;
  });

  // Format time (e.g., 125 -> 2:05)
  function formatTime(seconds) {
    const minutes = Math.floor(seconds / 60);
    const secs = Math.floor(seconds % 60);
    return `${minutes}:${secs < 10 ? '0' : ''}${secs}`;
  }
</script>
{{< /rawhtml >}}