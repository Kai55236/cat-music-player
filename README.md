# cat-music-player

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Cat Vibes Player</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(to bottom, #ffdefa, #ffe0f3);
      font-family: 'Comic Sans MS', cursive, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .player {
      background: #fff7fd;
      border-radius: 20px;
      padding: 30px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
      text-align: center;
      width: 300px;
      position: relative;
    }
    .circle {
      width: 120px;
      height: 120px;
      border: 10px solid #a6ffe3;
      border-radius: 50%;
      margin: 0 auto 20px;
      background: url('https://i.pinimg.com/originals/77/3f/c7/773fc7e00753a22a0d74b659704f0be5.gif') center center / cover;
    }
    .title {
      font-size: 18px;
      font-weight: bold;
      margin-bottom: 5px;
      color: #ff69b4;
    }
    .artist {
      font-size: 14px;
      color: #888;
      margin-bottom: 20px;
    }
    .controls {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin: 20px 0;
    }
    .controls button {
      background: none;
      border: none;
      font-size: 24px;
      cursor: pointer;
      color: #ff69b4;
    }
    iframe {
      display: none;
    }
  </style>
</head>
<body>
  <div class="player">
    <div class="circle"></div>
    <div class="title">Up Next</div>
    <div class="artist">DJ Catnip</div>
    <div class="controls">
      <button onclick="rewind()">⏮️</button>
      <button onclick="togglePlayPause()">⏯️</button>
      <button onclick="forward()">⏭️</button>
    </div>
    <iframe id="ytplayer" type="text/html" width="0" height="0"
      src="https://www.youtube.com/embed/yzFHfw1567o?autoplay=1&enablejsapi=1"
      frameborder="0" allow="autoplay"></iframe>
  </div>
  <script>
    let player;
    function onYouTubeIframeAPIReady() {
      player = new YT.Player('ytplayer');
    }

    function togglePlayPause() {
      if (player && player.getPlayerState() === 1) {
        player.pauseVideo();
      } else {
        player.playVideo();
      }
    }

    function rewind() {
      if (player) player.seekTo(0);
    }

    function forward() {
      if (player) player.seekTo(player.getDuration());
    }
  </script>
  <script src="https://www.youtube.com/iframe_api"></script>
</body>
</html>
