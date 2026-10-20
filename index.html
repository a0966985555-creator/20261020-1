<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>高中英文情境拖曳測驗系統</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- FontAwesome 圖示 CDN -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <!-- Canvas Confetti 彩帶效果庫 -->
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap');
    
    body {
      font-family: 'Plus Jakarta Sans', sans-serif, system-ui;
      background: linear-gradient(135deg, #f0f4f8 0%, #e2e8f0 100%);
      min-height: 100vh;
    }

    /* 拖曳目標區 Dash 樣式動畫 */
    .drop-zone {
      transition: all 0.25s ease;
      border: 2px dashed #94a3b8;
    }

    .drop-zone.drag-over {
      border-color: #3b82f6;
      background-color: #eff6ff;
      transform: scale(1.02);
      box-shadow: 0 8px 20px rgba(59, 130, 246, 0.15);
    }

    .drop-zone.filled {
      border-style: solid;
      border-color: #3b82f6;
      background-color: #f0f9ff;
    }

    /* 可拖曳物件樣式 */
    .draggable-item {
      cursor: grab;
      touch-action: none;
      user-select: none;
      transition: transform 0.2s, box-shadow 0.2s, background-color 0.2s;
    }

    .draggable-item:active {
      cursor: grabbing;
      transform: scale(1.03);
      box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.25);
    }

    .draggable-item.dragging {
      opacity: 0.4;
    }

    /* 全螢幕 Confetti Canvas */
    #confetti-canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      pointer-events: none;
      z-index: 9999;
    }

    /* 彈出視窗淡入效果 */
    .modal-backdrop {
      background: rgba(15, 23, 42, 0.65);
      backdrop-filter: blur(6px);
    }

    /* 自訂捲軸 */
    ::-webkit-scrollbar {
      width: 6px;
      height: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #f1f5f9;
    }
    ::-webkit-scrollbar-thumb {
      background: #cbd5e1;
      border-radius: 3px;
    }
  </style>
</head>
<body class="flex flex-col min-h-screen text-slate-800 antialiased">
  <!-- 全螢幕彩帶 Canvas -->
  <canvas id="confetti-canvas"></canvas>

  <!-- 主容器 -->
  <div class="flex-1 flex flex-col max-w-6xl w-full mx-auto px-4 py-6 md:py-8 justify-between">
    
    <!-- 頁頭資訊 -->
    <header class="text-center mb-6">
      <div class="inline-flex items-center gap-2 px-3.5 py-1.5 bg-blue-100 text-blue-700 rounded-full text-xs font-bold mb-2">
        <i class="fa-solid fa-file-csv"></i> CSV 隨機題庫系統 (抽 6 題)
      </div>
      <h1 class="text-2xl md:text-3xl font-extrabold text-slate-900 tracking-tight">
        High School English Context Matching Quiz
      </h1>
      <p class="text-xs md:text-sm text-slate-600 mt-1 max-w-xl mx-auto">
        系統會自動讀取同目錄下的 <code>questions.csv</code> 並隨機抽出 6 題！觀察動態 GIF 畫面或自訂繪製動畫，將正確選項拖曳至下方空格。
      </p>
      
      <!-- CSV 載入狀態指示標籤 -->
      <div id="status-badge" class="mt-2 text-xs font-semibold inline-flex items-center gap-1.5 px-3 py-1 rounded-md bg-slate-200 text-slate-700">
        <i class="fa-solid fa-spinner fa-spin"></i> 正在載入題庫中...
      </div>
    </header>

    <!-- 測驗主要內容區 (6 題格網) -->
    <main id="quiz-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5 mb-8">
      <!-- 由 JS 自動動態渲染 6 題卡片與動態 Canvas -->
    </main>

    <!-- 底部：拖曳選項庫與交卷按鈕區 -->
    <footer class="bg-white rounded-2xl p-5 shadow-lg border border-slate-200 sticky bottom-4 z-10">
      <div class="flex items-center justify-between mb-3">
        <h3 class="text-xs font-bold text-slate-500 uppercase tracking-wider flex items-center gap-1.5">
          <i class="fa-solid fa-layer-group text-blue-500"></i> 片語選項庫 (含 6 正確 + 6 干擾項，請拖曳或點擊填入)
        </h3>
        <span class="text-xs text-slate-400 hidden sm:inline">支援電腦拖曳 / 平板觸控 / 點擊填入</span>
      </div>

      <!-- 12 個選項容器 -->
      <div id="options-container" class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-2.5 mb-4 min-h-[80px]">
        <!-- JS 動態生成選項卡片 -->
      </div>

      <!-- 操作按鈕區 -->
      <div class="flex flex-col sm:flex-row items-center justify-between gap-3 pt-3 border-t border-slate-100">
        <div class="flex gap-2 w-full sm:w-auto">
          <button id="reset-answers-btn" class="flex-1 sm:flex-none px-4 py-2.5 rounded-xl border border-slate-300 text-slate-600 font-semibold hover:bg-slate-50 transition text-sm flex items-center justify-center gap-2">
            <i class="fa-solid fa-rotate-left"></i> 清空作答
          </button>
          <button id="repick-btn" class="flex-1 sm:flex-none px-4 py-2.5 rounded-xl border border-blue-300 bg-blue-50 text-blue-700 font-semibold hover:bg-blue-100 transition text-sm flex items-center justify-center gap-2">
            <i class="fa-solid fa-shuffle"></i> 重新抽題 (6題)
          </button>
        </div>
        
        <button id="submit-btn" class="w-full sm:w-auto px-8 py-3 rounded-xl bg-gradient-to-r from-blue-600 to-indigo-600 text-white font-bold hover:from-blue-700 hover:to-indigo-700 active:scale-95 transition shadow-lg shadow-blue-500/25 text-base flex items-center justify-center gap-2">
          <i class="fa-solid fa-paper-plane"></i> 交卷看成績
        </button>
      </div>
    </footer>
  </div>

  <!-- 成績結算 Modal 彈出視窗 -->
  <div id="result-modal" class="fixed inset-0 z-50 modal-backdrop flex items-center justify-center p-4 hidden opacity-0 transition-opacity duration-300">
    <div class="bg-white rounded-3xl max-w-lg w-full p-6 md:p-8 shadow-2xl border border-slate-100 text-center transform scale-95 transition-transform duration-300 overflow-y-auto max-h-[90vh]" id="modal-card">
      
      <!-- 圖示與標題 -->
      <div id="modal-icon-container" class="w-20 h-20 rounded-full mx-auto flex items-center justify-center mb-4 text-3xl shadow-inner">
        <!-- 動態渲染圖示 -->
      </div>
      
      <h2 id="modal-title" class="text-2xl font-extrabold text-slate-900 mb-1">測驗總成績結算</h2>
      <p id="modal-subtitle" class="text-xs text-slate-500 mb-5">High School English Drag & Drop Quiz Result</p>

      <!-- 得分大字區 -->
      <div class="bg-slate-50 rounded-2xl p-4 mb-5 border border-slate-100">
        <div class="text-xs text-slate-400 font-bold uppercase mb-1">得分百分比 (Score)</div>
        <div class="flex items-baseline justify-center gap-1">
          <span id="score-percentage" class="text-5xl font-black text-slate-800">0</span>
          <span class="text-2xl font-bold text-slate-400">%</span>
        </div>
        <div id="score-detail" class="text-xs text-slate-500 mt-2 font-semibold">
          答對 0 / 6 題
        </div>
      </div>

      <!-- 詳細檢討列表 -->
      <div class="text-left mb-6">
        <h4 class="text-xs font-bold text-slate-400 uppercase tracking-wider mb-2">題型與答案檢討：</h4>
        <div id="review-list" class="space-y-2 text-xs">
          <!-- JS 動態插入檢討細節 -->
        </div>
      </div>

      <!-- 按鈕區域 -->
      <div class="flex gap-3">
        <button id="modal-restart-btn" class="w-full py-3 px-4 bg-slate-900 hover:bg-slate-800 text-white rounded-xl font-bold transition shadow-md active:scale-95 text-sm flex items-center justify-center gap-2">
          <i class="fa-solid fa-shuffle"></i> 重新抽題再測一次
        </button>
      </div>
    </div>
  </div>

  <!-- JavaScript 邏輯 -->
  <script>
    // 預設 CSV 題庫資料 (備用：當找不到 questions.csv 或網路離線時自動載入)
    const DEFAULT_CSV_DATA = `id,type,context,sentence,answer,distractor,gif_url
1,book,書桌前專心苦讀,Students need to ______ diligently for the exam.,hit the books,play video games,https://media2.giphy.com/media/v1.Y2lkPTZjMDliOTUyNmJ4djQxODY2b21jMnY3Zjk5N3hxMzB0NzlvejBtajBmaHhqN29hNCZlcD12MV9naWZzX3NlYXJjaCZjdD1n/6XX4V0O8a0xdS/giphy.gif
2,sports,規律健身與體能訓練,Doctors advise people to ______ every week.,stay in shape,couch potato,https://cdn.dribbble.com/userupload/21279962/file/original-8ae58dbd5d6c82681a77569e5d422822.gif
3,presentation,台上公開演講發表,The student prepared carefully to ______ in class.,give a presentation,whisper softly,https://cdnl.iconscout.com/lottie/premium/thumb/public-speaking-animation-gif-download-5455333.gif
4,brainstorm,團隊腦力激盪討論,Team members met together to ______ for the project.,brainstorm ideas,quarrel loudly,https://cdn.dribbble.com/userupload/36622164/file/original-b61c60cf62db49843fd3a4da06f0b35a.gif
5,flight,搭乘飛機出國旅遊,They plan to ______ after graduation to see the world.,catch a flight,miss the bus,https://cdn.dribbble.com/userupload/22925124/file/original-d06f15354921d8a6cf5e9782335c199a.gif
6,trophy,獲得獎盃慶祝榮耀,After hard work, the team managed to ______.,win first place,give up halfway,https://www.presentermedia.com/cfdownload/36280?sourceButton=lgGIFwhite
7,book,圖書館查閱參考書籍,She stayed up late to ______ for her final essay.,burn the midnight oil,sleep early,
8,sports,戶外晨跑鍛鍊身體,He goes running every morning to ______.,keep fit,eat junk food,
9,brainstorm,團隊合作提出解方,We need to think together to ______ for this problem.,come up with solutions,ignore the issue,
10,flight,登機準備出發,Passengers should be ready to ______ on time.,board the plane,cancel the ticket,`;

    // 全域變數
    let fullQuestionBank = [];  // 完整題庫
    let currentQuestions = [];  // 當前抽出的 6 題
    let draggedElement = null;
    let touchDraggedElement = null;
    let touchClone = null;
    let animFrameIds = [];

    // DOM 元素引用
    const quizGrid = document.getElementById('quiz-grid');
    const optionsContainer = document.getElementById('options-container');
    const statusBadge = document.getElementById('status-badge');
    const submitBtn = document.getElementById('submit-btn');
    const resetAnswersBtn = document.getElementById('reset-answers-btn');
    const repickBtn = document.getElementById('repick-btn');
    const resultModal = document.getElementById('result-modal');
    const modalCard = document.getElementById('modal-card');
    const modalRestartBtn = document.getElementById('modal-restart-btn');

    // CSV 解析工具函式 (支援引號與逗號)
    function parseCSV(csvText) {
      const lines = csvText.trim().split('\n');
      if (lines.length < 2) return [];

      const result = [];
      for (let i = 1; i < lines.length; i++) {
        if (!lines[i].trim()) continue;
        
        const values = lines[i].match(/(".*?"|[^",\s]+)(?=\s*,|\s*$)/g) || lines[i].split(',');
        const cleaned = values.map(val => val.replace(/^"|"$/g, '').trim());

        if (cleaned.length >= 5) {
          result.push({
            id: cleaned[0] || `q-${i}`,
            type: cleaned[1] || 'book',
            context: cleaned[2] || '情境描述',
            sentence: cleaned[3] || '',
            answer: cleaned[4] || '',
            distractor: cleaned[5] || 'distractor option',
            gif_url: cleaned[6] || ''
          });
        }
      }
      return result;
    }

    // 非同步載入 CSV 題庫
    async function loadQuestionsCSV() {
      try {
        const response = await fetch('questions.csv');
        if (!response.ok) throw new Error('HTTP error: ' + response.status);
        const csvText = await response.text();
        fullQuestionBank = parseCSV(csvText);

        if (fullQuestionBank.length < 6) throw new Error('題庫不足 6 題');

        statusBadge.className = "mt-2 text-xs font-semibold inline-flex items-center gap-1.5 px-3 py-1 rounded-md bg-green-100 text-green-700";
        statusBadge.innerHTML = `<i class="fa-solid fa-circle-check"></i> 已成功載入外部 CSV 題庫 (共 ${fullQuestionBank.length} 題)`;
      } catch (err) {
        console.warn('無法讀取外部 questions.csv，切換為內建題庫:', err);
        fullQuestionBank = parseCSV(DEFAULT_CSV_DATA);

        statusBadge.className = "mt-2 text-xs font-semibold inline-flex items-center gap-1.5 px-3 py-1 rounded-md bg-amber-100 text-amber-700";
        statusBadge.innerHTML = `<i class="fa-solid fa-triangle-exclamation"></i> 使用預備題庫 (共 ${fullQuestionBank.length} 題)`;
      }

      pickRandomQuiz();
    }

    // 隨機抽取 6 題並建立畫面
    function pickRandomQuiz() {
      if (fullQuestionBank.length === 0) return;

      const shuffled = [...fullQuestionBank].sort(() => Math.random() - 0.5);
      currentQuestions = shuffled.slice(0, 6);

      renderQuizCards();
      renderOptionCards();
      closeModal();
    }

    // 渲染 6 個題目卡片
    function renderQuizCards() {
      quizGrid.innerHTML = '';
      
      // 清理前一輪動畫循環
      animFrameIds.forEach(id => cancelAnimationFrame(id));
      animFrameIds = [];

      currentQuestions.forEach((q, idx) => {
        const card = document.createElement('div');
        card.className = 'bg-white rounded-2xl p-4 shadow-sm border border-slate-200 flex flex-col justify-between hover:shadow-md transition';
        
        const formattedSentence = q.sentence.replace('______', '<span class="underline decoration-blue-500 font-bold px-1 text-blue-600">______</span>');

        card.innerHTML = `
          <div>
            <div class="w-full h-44 rounded-xl bg-slate-900 flex items-center justify-center relative overflow-hidden mb-3 border border-slate-200" id="media-container-${idx}">
              <span class="absolute top-2 left-2 bg-black/60 backdrop-blur-sm text-white text-xs px-2 py-0.5 rounded font-mono font-bold z-10">Q${idx + 1}</span>
            </div>
            <p class="text-xs text-blue-600 mb-1 font-bold"><i class="fa-solid fa-compass"></i> 情境：${q.context}</p>
            <p class="text-xs text-slate-700 mb-3 leading-relaxed font-medium">${formattedSentence}</p>
          </div>
          <div class="drop-zone w-full h-12 rounded-xl flex items-center justify-center p-2 relative bg-slate-50/60" data-qid="${q.id}">
            <span class="placeholder-text text-slate-400 text-xs font-medium pointer-events-none flex items-center gap-1">
              <i class="fa-regular fa-hand-pointer"></i> 拖曳答案至此
            </span>
          </div>
        `;

        quizGrid.appendChild(card);

        // 媒體處理：嘗試載入 GIF，若無 URL 或載入失敗則觸發 Canvas 動畫繪製引擎
        const mediaContainer = card.querySelector(`#media-container-${idx}`);
        if (q.gif_url && q.gif_url.trim() !== '') {
          const img = new Image();
          img.src = q.gif_url;
          img.className = 'w-full h-full object-cover';
          img.alt = `Q${idx + 1} GIF`;
          img.onload = () => mediaContainer.appendChild(img);
          img.onerror = () => generateCanvasAnimation(mediaContainer, q.type, idx);
        } else {
          generateCanvasAnimation(mediaContainer, q.type, idx);
        }
      });

      bindDropZoneEvents();
    }

    // 渲染 12 個選項卡片 (6 個正確答案 + 6 個干擾答案)
    function renderOptionCards() {
      optionsContainer.innerHTML = '';

      let optionList = [];
      currentQuestions.forEach(q => {
        optionList.push({ qid: q.id, text: q.answer, isCorrect: true });
        optionList.push({ qid: `distractor-${q.id}`, text: q.distractor, isCorrect: false });
      });

      // 隨機打亂 12 個選項
      optionList.sort(() => Math.random() - 0.5);

      optionList.forEach(opt => {
        const optEl = createDraggableElement(opt);
        optionsContainer.appendChild(optEl);
      });
    }

    // 建立可拖曳選項 DOM 元素
    function createDraggableElement(item) {
      const el = document.createElement('div');
      el.className = 'draggable-item bg-slate-800 hover:bg-slate-700 text-white font-medium py-2 px-2.5 rounded-xl text-center shadow border border-slate-700 text-xs flex items-center justify-center';
      el.setAttribute('draggable', 'true');
      el.dataset.qid = item.qid;
      el.dataset.text = item.text;
      
      el.innerHTML = `<span>${item.text}</span>`;

      // 1. Desktop Drag & Drop
      el.addEventListener('dragstart', handleDragStart);
      el.addEventListener('dragend', handleDragEnd);

      // 2. Mobile Touch Events
      el.addEventListener('touchstart', handleTouchStart, { passive: false });
      el.addEventListener('touchmove', handleTouchMove, { passive: false });
      el.addEventListener('touchend', handleTouchEnd);

      // 3. 點擊快速填入/歸還
      el.addEventListener('click', handleQuickClick);

      return el;
    }

    // 綁定 Drop Zone 事件
    function bindDropZoneEvents() {
      const dropZones = document.querySelectorAll('.drop-zone');
      dropZones.forEach(zone => {
        zone.addEventListener('dragover', (e) => {
          e.preventDefault();
          e.dataTransfer.dropEffect = 'move';
          zone.classList.add('drag-over');
        });

        zone.addEventListener('dragleave', () => zone.classList.remove('drag-over'));

        zone.addEventListener('drop', (e) => {
          e.preventDefault();
          zone.classList.remove('drag-over');
          if (draggedElement) placeItemInZone(draggedElement, zone);
        });
      });
    }

    // ==================== 電腦端 Drag & Drop ====================
    function handleDragStart(e) {
      draggedElement = this;
      this.classList.add('dragging');
      e.dataTransfer.setData('text/plain', this.dataset.qid);
      e.dataTransfer.effectAllowed = 'move';
    }

    function handleDragEnd() {
      this.classList.remove('dragging');
      draggedElement = null;
    }

    // ==================== 行動裝置 Touch Events ====================
    function handleTouchStart(e) {
      touchDraggedElement = this;
      const touch = e.touches[0];
      
      touchClone = this.cloneNode(true);
      touchClone.style.position = 'fixed';
      touchClone.style.zIndex = '1000';
      touchClone.style.opacity = '0.9';
      touchClone.style.pointerEvents = 'none';
      touchClone.style.width = `${this.offsetWidth}px`;
      touchClone.style.left = `${touch.clientX - this.offsetWidth / 2}px`;
      touchClone.style.top = `${touch.clientY - touchClone.offsetHeight / 2}px`;
      document.body.appendChild(touchClone);

      this.classList.add('opacity-40');
    }

    function handleTouchMove(e) {
      if (!touchClone) return;
      e.preventDefault();

      const touch = e.touches[0];
      touchClone.style.left = `${touch.clientX - touchClone.offsetWidth / 2}px`;
      touchClone.style.top = `${touch.clientY - touchClone.offsetHeight / 2}px`;

      const elementUnderTouch = document.elementFromPoint(touch.clientX, touch.clientY);
      const dropZones = document.querySelectorAll('.drop-zone');
      dropZones.forEach(zone => {
        if (zone.contains(elementUnderTouch)) zone.classList.add('drag-over');
        else zone.classList.remove('drag-over');
      });
    }

    function handleTouchEnd(e) {
      if (!touchDraggedElement) return;

      if (touchClone) {
        touchClone.remove();
        touchClone = null;
      }

      touchDraggedElement.classList.remove('opacity-40');

      const touch = e.changedTouches[0];
      const elementUnderTouch = document.elementFromPoint(touch.clientX, touch.clientY);
      const dropZones = document.querySelectorAll('.drop-zone');

      dropZones.forEach(zone => {
        zone.classList.remove('drag-over');
        if (zone.contains(elementUnderTouch)) {
          placeItemInZone(touchDraggedElement, zone);
        }
      });

      touchDraggedElement = null;
    }

    // ==================== 點擊交互 ====================
    function handleQuickClick() {
      if (this.parentElement.classList.contains('drop-zone')) {
        const parentZone = this.parentElement;
        optionsContainer.appendChild(this);
        checkZoneState(parentZone);
        return;
      }

      const dropZones = document.querySelectorAll('.drop-zone');
      const emptyZone = Array.from(dropZones).find(zone => !zone.querySelector('.draggable-item'));
      if (emptyZone) {
        placeItemInZone(this, emptyZone);
      }
    }

    // 放置卡片核心邏輯
    function placeItemInZone(item, zone) {
      const existingItem = zone.querySelector('.draggable-item');
      if (existingItem) {
        optionsContainer.appendChild(existingItem);
      }

      const oldZone = item.parentElement.classList.contains('drop-zone') ? item.parentElement : null;

      zone.appendChild(item);
      checkZoneState(zone);

      if (oldZone && oldZone !== zone) {
        checkZoneState(oldZone);
      }
    }

    // 更新 Drop Zone DOM 狀態
    function checkZoneState(zone) {
      const hasItem = zone.querySelector('.draggable-item');
      const placeholder = zone.querySelector('.placeholder-text');

      if (hasItem) {
        zone.classList.add('filled');
        if (placeholder) placeholder.style.display = 'none';
      } else {
        zone.classList.remove('filled');
        if (placeholder) placeholder.style.display = 'flex';
      }
    }

    // 清空作答
    function resetCurrentAnswers() {
      const dropZones = document.querySelectorAll('.drop-zone');
      dropZones.forEach(zone => {
        const item = zone.querySelector('.draggable-item');
        if (item) optionsContainer.appendChild(item);
        checkZoneState(zone);
      });
    }

    // ==================== Canvas 繪圖備援引擎 ====================
    function generateCanvasAnimation(container, type, idx) {
      container.innerHTML = '';
      const canvas = document.createElement('canvas');
      canvas.className = 'w-full h-full';
      container.appendChild(canvas);

      const ctx = canvas.getContext('2d');
      let width = canvas.width = container.clientWidth || 300;
      let height = canvas.height = container.clientHeight || 180;

      let frame = 0;

      function animate() {
        frame++;
        ctx.clearRect(0, 0, width, height);

        // 繪製科技漸層背景
        let bgGrad = ctx.createLinearGradient(0, 0, 0, height);
        bgGrad.addColorStop(0, '#0f172a');
        bgGrad.addColorStop(1, '#1e293b');
        ctx.fillStyle = bgGrad;
        ctx.fillRect(0, 0, width, height);

        ctx.save();
        ctx.translate(width / 2, height / 2);

        if (type === 'book') {
          // 1. 書本翻頁動畫
          let swing = Math.sin(frame * 0.05) * 5;
          ctx.fillStyle = '#f59e0b';
          ctx.fillRect(-45, -35 + swing, 90, 60);
          ctx.fillStyle = '#ffffff';
          ctx.fillRect(-40, -30 + swing, 36, 50);
          ctx.fillRect(4, -30 + swing, 36, 50);

          let pageTurn = Math.abs(Math.sin(frame * 0.08)) * 30;
          ctx.fillStyle = '#cbd5e1';
          ctx.beginPath();
          ctx.moveTo(0, -30 + swing);
          ctx.lineTo(-pageTurn, 20 + swing);
          ctx.lineTo(0, 20 + swing);
          ctx.fill();
        } else if (type === 'sports') {
          // 2. 運動跳繩小人動畫
          let bounce = Math.abs(Math.sin(frame * 0.1)) * 16;
          ctx.fillStyle = '#38bdf8';
          ctx.beginPath();
          ctx.arc(0, -25 - bounce, 14, 0, Math.PI * 2);
          ctx.fill();

          ctx.strokeStyle = '#38bdf8';
          ctx.lineWidth = 4;
          ctx.beginPath();
          ctx.moveTo(0, -10 - bounce);
          ctx.lineTo(0, 20 - bounce);
          ctx.lineTo(-14, 40 - bounce);
          ctx.moveTo(0, 20 - bounce);
          ctx.lineTo(14, 40 - bounce);
          ctx.stroke();

          ctx.strokeStyle = '#f43f5e';
          ctx.lineWidth = 2.5;
          ctx.beginPath();
          ctx.ellipse(0, 15 - bounce, 40, 10 + Math.sin(frame * 0.2) * 5, 0, 0, Math.PI * 2);
          ctx.stroke();
        } else if (type === 'presentation') {
          // 3. 演講與跳動簡報圖表
          ctx.fillStyle = '#334155';
          ctx.fillRect(-55, -45, 110, 65);
          ctx.fillStyle = '#ffffff';
          ctx.fillRect(-50, -40, 100, 55);

          ctx.fillStyle = '#ef4444';
          let h1 = Math.abs(Math.sin(frame * 0.05)) * 30;
          ctx.fillRect(-35, 10 - h1, 12, h1);
          ctx.fillStyle = '#3b82f6';
          let h2 = Math.abs(Math.sin(frame * 0.05 + 1)) * 30;
          ctx.fillRect(-15, 10 - h2, 12, h2);
          ctx.fillStyle = '#10b981';
          let h3 = Math.abs(Math.sin(frame * 0.05 + 2)) * 30;
          ctx.fillRect(5, 10 - h3, 12, h3);
        } else if (type === 'brainstorm') {
          // 4. 腦力激盪發光燈泡
          let pulse = 18 + Math.sin(frame * 0.1) * 3;
          ctx.fillStyle = '#facc15';
          ctx.beginPath();
          ctx.arc(0, -8, pulse, 0, Math.PI * 2);
          ctx.fill();

          ctx.fillStyle = '#ca8a04';
          ctx.fillRect(-6, -8 + pulse - 3, 12, 10);
        } else if (type === 'flight') {
          // 5. 穿雲飛機動畫
          let planeY = Math.sin(frame * 0.05) * 8;
          ctx.fillStyle = '#e2e8f0';
          ctx.beginPath();
          ctx.ellipse(0, planeY, 38, 10, -0.2, 0, Math.PI * 2);
          ctx.fill();

          ctx.fillStyle = '#38bdf8';
          ctx.beginPath();
          ctx.moveTo(-8, planeY);
          ctx.lineTo(-20, planeY - 24);
          ctx.lineTo(4, planeY);
          ctx.fill();
        } else {
          // 6. 閃耀金黃獎盃
          ctx.fillStyle = '#fbbf24';
          ctx.beginPath();
          ctx.arc(0, -15, 24, 0, Math.PI);
          ctx.fill();

          ctx.fillRect(-6, -15, 12, 30);
          ctx.fillRect(-20, 15, 40, 8);
        }

        ctx.restore();
        const animId = requestAnimationFrame(animate);
        animFrameIds.push(animId);
      }

      animate();
    }

    // ==================== 交卷與結算分數 ====================
    function calculateScore() {
      const dropZones = document.querySelectorAll('.drop-zone');
      let correctCount = 0;
      const totalCount = currentQuestions.length;
      const reviewDetails = [];

      dropZones.forEach((zone, idx) => {
        const item = zone.querySelector('.draggable-item');
        const correctQ = currentQuestions[idx];
        const qNum = `Q${idx + 1}`;

        const isCorrect = item && item.dataset.qid === correctQ.id;
        if (isCorrect) correctCount++;

        const userText = item ? item.dataset.text : '（未作答）';

        reviewDetails.push({
          qNum,
          isCorrect,
          userText,
          correctText: correctQ.answer
        });
      });

      const percentage = Math.round((correctCount / totalCount) * 100);
      showResultModal(correctCount, totalCount, percentage, reviewDetails);
    }

    // 顯示結算視窗
    function showResultModal(correct, total, percentage, reviewDetails) {
      const modalIconContainer = document.getElementById('modal-icon-container');
      const scorePercentage = document.getElementById('score-percentage');
      const scoreDetail = document.getElementById('score-detail');
      const reviewList = document.getElementById('review-list');

      scorePercentage.textContent = percentage;
      scoreDetail.textContent = `答對 ${correct} / ${total} 題`;

      reviewList.innerHTML = reviewDetails.map(item => `
        <div class="p-2.5 rounded-lg border flex flex-col sm:flex-row sm:items-center justify-between gap-1 ${item.isCorrect ? 'bg-green-50/70 border-green-200 text-green-900' : 'bg-red-50/70 border-red-200 text-red-900'}">
          <div class="flex items-center gap-1.5">
            <span class="font-bold font-mono text-slate-700">${item.qNum}:</span>
            <span>你的答案: <strong class="underline">${item.userText}</strong></span>
          </div>
          <div>
            ${item.isCorrect 
              ? '<span class="text-green-600 font-bold flex items-center gap-1"><i class="fa-solid fa-circle-check"></i> 正確</span>' 
              : `<span class="text-red-600 font-bold flex items-center gap-1"><i class="fa-solid fa-circle-xmark"></i> 正解: ${item.correctText}</span>`}
          </div>
        </div>
      `).join('');

      // 成績 >= 60% 觸發全螢幕彩帶效果
      const isPassed = percentage >= 60;

      if (isPassed) {
        modalIconContainer.className = "w-20 h-20 rounded-full mx-auto flex items-center justify-center mb-4 text-3xl bg-green-100 text-green-600 shadow-inner";
        modalIconContainer.innerHTML = `<i class="fa-solid fa-trophy"></i>`;
        triggerConfetti();
      } else {
        modalIconContainer.className = "w-20 h-20 rounded-full mx-auto flex items-center justify-center mb-4 text-3xl bg-amber-100 text-amber-600 shadow-inner";
        modalIconContainer.innerHTML = `<i class="fa-solid fa-book-open"></i>`;
      }

      resultModal.classList.remove('hidden');
      setTimeout(() => {
        resultModal.classList.remove('opacity-0');
        modalCard.classList.remove('scale-95');
        modalCard.classList.add('scale-100');
      }, 10);
    }

    // 關閉 Modal
    function closeModal() {
      resultModal.classList.add('opacity-0');
      modalCard.classList.remove('scale-100');
      modalCard.classList.add('scale-95');
      setTimeout(() => {
        resultModal.classList.add('hidden');
      }, 300);
    }

    // 全螢幕彩帶動畫 (Confetti Animation)
    function triggerConfetti() {
      const myCanvas = document.getElementById('confetti-canvas');
      const customConfetti = confetti.create(myCanvas, {
        resize: true,
        useWorker: true
      });

      const duration = 3 * 1000;
      const animationEnd = Date.now() + duration;

      const interval = setInterval(function() {
        const timeLeft = animationEnd - Date.now();
        if (timeLeft <= 0) return clearInterval(interval);

        const particleCount = 50 * (timeLeft / duration);
        customConfetti({
          particleCount: particleCount / 2,
          startVelocity: 35,
          spread: 360,
          origin: { x: Math.random(), y: Math.random() - 0.2 }
        });
      }, 250);
    }

    // 事件按鈕綁定
    submitBtn.addEventListener('click', calculateScore);
    resetAnswersBtn.addEventListener('click', resetCurrentAnswers);
    repickBtn.addEventListener('click', pickRandomQuiz);
    modalRestartBtn.addEventListener('click', pickRandomQuiz);

    // 初次載入
    window.addEventListener('DOMContentLoaded', loadQuestionsCSV);
  </script>
</body>
</html>