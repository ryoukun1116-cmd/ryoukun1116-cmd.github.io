# ryoukun1116-cmd.github.io
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <title>シンプル掲示板</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      margin: 0;
      padding: 20px;
    }
    h1 { text-align: center; }
    .board {
      max-width: 600px;
      margin: 0 auto;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    input, textarea, button {
      width: 100%;
      margin-bottom: 10px;
      padding: 8px;
      font-size: 14px;
    }
    button {
      background: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
    }
    button:hover { opacity: 0.9; }
    .post {
      border-bottom: 1px solid #ddd;
      padding: 10px 0;
    }
    .name { font-weight: bold; }
    .time { font-size: 12px; color: #777; }
  </style>
</head>
<body>
  <h1>掲示板</h1>
  <div class="board">
    <input id="name" placeholder="名前" />
    <textarea id="message" placeholder="書き込み内容"></textarea>
    <button onclick="addPost()">投稿</button>
    <div id="posts"></div>
  </div>

  <script>
    function addPost() {
      const name = document.getElementById('name').value || '名無し';
      const message = document.getElementById('message').value;
      if (!message) return;

      const post = document.createElement('div');
      post.className = 'post';

      const time = new Date().toLocaleString();
      post.innerHTML = `<div class="name">${name}</div>
                        <div>${message}</div>
                        <div class="time">${time}</div>`;

      document.getElementById('posts').prepend(post);
      document.getElementById('message').value = '';
    }
  </script>
</body>
</html>
