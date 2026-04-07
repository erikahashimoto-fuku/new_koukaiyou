# 散歩記録アプリ
<div class="input-area">
    <input type="text" id="location" placeholder="どこを歩いた？">
    <textarea id="memo" placeholder="感想や発見をメモしてね"></textarea>
    <button onclick="saveWalk()">記録する！</button>
</div>

<div id="recordList">
    </div>

<style>
    body { font-family: sans-serif; padding: 20px; background-color: #f0f9ff; }
    .input-area { background: white; padding: 20px; border-radius: 10px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
    input, textarea { width: 100%; display: block; margin-bottom: 10px; padding: 10px; border: 1px solid #ccc; border-radius: 5px; }
    button { width: 100%; padding: 10px; background: #4caf50; color: white; border: none; border-radius: 5px; cursor: pointer; }
    .record-card { background: white; margin-top: 10px; padding: 15px; border-radius: 8px; border-left: 5px solid #4caf50; }
</style>
<script>
    function saveWalk() {
        const loc = document.getElementById('location').value;
        const mem = document.getElementById('memo').value;
        const time = new Date().toLocaleString();

        if (loc === "") {
            alert("場所を入力してね！");
            return;
        }

        // 記録を表示するための新しい箱を作る
        const card = document.createElement('div');
        card.className = 'record-card';
        card.innerHTML = `<strong>${time}</strong><br>📍 ${loc}<p>${mem}</p>`;

        // リストの一番上に追加する
        const list = document.getElementById('recordList');
        list.insertBefore(card, list.firstChild);

        // 入力欄を空っぽにする
        document.getElementById('location').value = "";
        document.getElementById('memo').value = "";
    }
</script>