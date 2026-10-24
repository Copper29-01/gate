<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>作业滞销帮帮我们！</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
    }

    :root {
      --bg-body: #f2f4f6;
      --bg-app: #fbfcfd;
      --text-primary: #1a1d21;
      --text-secondary: #838b93;
      --text-muted: #b0b8c0;
      --option-bg: #f1f4f7;
      --option-border: #e2e7ec;
      --option-shadow: #dce2e8;
      --option-hover: #e8edf2;
      --option-selected-bg: #1a1d21;
      --option-selected-text: #fbfcfd;
      --progress-track: #e8edf2;
      --progress-fill: #1a1d21;
      --border-light: #e6ebf0;
      --dialog-bg: #fbfcfd;
      --dialog-border: #e6ebf0;
      --btn-bg: #1a1d21;
      --btn-text: #fbfcfd;
      --btn-hover: #2c3036;
      --intro-bg: #f6f8fa;
      --intro-border: #e9eef3;
      --door-border: #1a1d21;
      --door-fill: #fbfcfd;
    }

    body.dark-mode {
      --bg-body: #000000;
      --bg-app: #000000;
      --text-primary: #e8ecf0;
      --text-secondary: #9aa3ad;
      --text-muted: #5a626b;
      --option-bg: #101317;
      --option-border: #272d34;
      --option-shadow: #05070a;
      --option-hover: #1a1f25;
      --option-selected-bg: #e8ecf0;
      --option-selected-text: #000000;
      --progress-track: #16191d;
      --progress-fill: #e8ecf0;
      --border-light: #272d34;
      --dialog-bg: #0a0c0f;
      --dialog-border: #272d34;
      --btn-bg: #e8ecf0;
      --btn-text: #000000;
      --btn-hover: #f5f7fa;
      --intro-bg: #0a0c0f;
      --intro-border: #272d34;
      --door-border: #cfd6dd;
      --door-fill: #000000;
    }

    body {
      background: var(--bg-body);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      transition: background 0.4s;
    }

    .app {
      width: 100%;
      max-width: 480px;
      min-height: 80vh;
      background: var(--bg-app);
      border-radius: 36px;
      box-shadow: 0 12px 30px rgba(0, 0, 0, 0.06);
      padding: 24px 20px;
      display: flex;
      flex-direction: column;
      position: relative;
      overflow: hidden;
      transition: background 0.4s, box-shadow 0.4s, color 0.4s;
    }

    .app.dark-mode {
      box-shadow: 0 12px 30px rgba(0, 0, 0, 0.8);
    }

    .hero-title,
    .question-header,
    .end-title {
      color: var(--text-primary);
    }

    .hero-sub,
    .end-sub {
      color: var(--text-secondary);
    }

    .intro-text {
      background: var(--intro-bg);
      border-color: var(--intro-border);
      color: var(--text-primary);
    }

    .option {
      background: var(--option-bg);
      border-color: var(--option-border);
      box-shadow: 0 2px 0 var(--option-shadow);
      color: var(--text-primary);
    }

    .option:hover {
      background: var(--option-hover);
    }

    .option.selected {
      background: var(--option-selected-bg);
      color: var(--option-selected-text);
      border-color: var(--option-selected-bg);
      box-shadow: 0 2px 0 #000;
    }

    .placeholder-space {
      border-color: var(--border-light);
      color: var(--text-muted);
    }

    .progress-track {
      background: var(--progress-track);
    }

    .progress-fill {
      background: var(--progress-fill);
    }

    .progress-text {
      color: var(--text-muted);
    }

    .question-mark {
      color: var(--text-primary);
      text-shadow: 0 2px 5px rgba(0, 0, 0, 0.06);
    }

    .btn {
      background: var(--btn-bg);
      color: var(--btn-text);
      border-color: var(--btn-bg);
    }

    .btn:hover {
      background: var(--btn-hover);
    }

    .btn-outline {
      background: transparent;
      color: var(--text-primary);
      border-color: var(--text-primary);
      box-shadow: none;
    }

    .btn-outline:hover {
      background: var(--option-bg);
    }

    .dialog {
      background: var(--dialog-bg);
      border-color: var(--dialog-border);
    }

    .dialog p {
      color: var(--text-primary);
    }

    .change-highlight {
      color: #ff3b3b;
      font-weight: 800;
      display: inline-block;
      animation: changeTremble 0.35s infinite;
      cursor: pointer;
      transition: color 0.3s ease;
    }

    @keyframes changeTremble {
      0%   { transform: translate(0, 0) rotate(0deg); }
      15%  { transform: translate(-2px, 1px) rotate(-2deg); }
      30%  { transform: translate(2px, -1px) rotate(2deg); }
      45%  { transform: translate(-1.5px, 0.5px) rotate(-1.5deg); }
      60%  { transform: translate(1.5px, -0.5px) rotate(1.5deg); }
      75%  { transform: translate(-1px, 1px) rotate(-1deg); }
      90%  { transform: translate(1px, -1px) rotate(1deg); }
      100% { transform: translate(0, 0) rotate(0deg); }
    }

    .change-highlight.stopped {
      animation: none;
      transform: none;
      color: var(--text-primary);
    }

    .app.dark-mode .change-highlight.stopped {
      color: #000000;
    }

    .app.dark-mode .change-highlight:not(.stopped) {
      color: #ff5a5a;
    }

    .progress-container {
      width: 100%;
      margin-bottom: 16px;
      padding: 0 4px;
      display: none;
    }

    .progress-container.active {
      display: block;
    }

    .progress-track {
      width: 100%;
      height: 8px;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.04);
    }

    .progress-fill {
      height: 100%;
      width: 0%;
      border-radius: 10px;
      transition: width 0.35s ease;
    }

    .progress-text {
      font-size: 0.8rem;
      text-align: right;
      margin-top: 4px;
      padding-right: 2px;
      letter-spacing: 0.5px;
    }

    .overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.85);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s ease;
      padding: 20px;
      flex-direction: column;
    }

    .overlay.active {
      opacity: 1;
      pointer-events: auto;
    }

    .dialog {
      border-radius: 32px;
      padding: 32px 24px;
      max-width: 360px;
      width: 100%;
      text-align: center;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
      border: 1px solid;
    }

    .dialog p {
      font-size: 1.25rem;
      line-height: 1.6;
      margin-bottom: 28px;
      font-weight: 500;
      letter-spacing: 0.3px;
    }

    .typewriter-dialog p {
      text-align: left;
      white-space: pre-wrap;
      min-height: 160px;
      font-size: 1.15rem;
      line-height: 1.7;
    }

    .btn {
      border: none;
      border-radius: 60px;
      padding: 16px 28px;
      font-size: 1.1rem;
      font-weight: 600;
      letter-spacing: 0.5px;
      cursor: pointer;
      transition: background 0.2s, transform 0.1s, opacity 0.2s;
      box-shadow: 0 4px 0 #00000030;
      width: 100%;
      max-width: 240px;
      margin: 0 auto;
      display: block;
      outline: none;
      border: 1px solid;
    }

    .btn:active {
      transform: translateY(2px);
      box-shadow: 0 1px 0 #00000030;
    }

    .btn-small {
      padding: 12px 22px;
      font-size: 1rem;
      width: auto;
      min-width: 120px;
      margin: 0 auto;
    }

    .btn-white {
      background: var(--dialog-bg);
      color: var(--text-primary);
      border-color: var(--text-primary);
      box-shadow: 0 4px 0 #00000020;
    }

    .btn-white:hover {
      background: var(--option-bg);
    }

    .page {
      display: none;
      flex-direction: column;
      flex: 1;
    }

    .page.active {
      display: flex;
    }

    .hero-title {
      font-size: 2.6rem;
      font-weight: 800;
      line-height: 1.2;
      margin-top: 15vh;
      margin-bottom: 12px;
      letter-spacing: -0.5px;
      text-align: left;
      padding-left: 8px;
    }

    .hero-sub {
      font-size: 1rem;
      margin-bottom: 48px;
      padding-left: 8px;
    }

    .intro-text {
      font-size: 1.15rem;
      line-height: 1.7;
      margin: 40px 0 30px;
      padding: 24px 20px;
      text-align: left;
      border-radius: 24px;
      border: 1px solid;
    }

    .question-header {
      font-size: 1.4rem;
      font-weight: 700;
      margin-bottom: 24px;
      margin-top: 12px;
      text-align: left;
      border-left: 6px solid var(--text-primary);
      padding-left: 16px;
    }

    .options {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-bottom: 24px;
    }

    .option {
      border-radius: 60px;
      padding: 16px 22px;
      font-size: 1.1rem;
      font-weight: 500;
      cursor: pointer;
      transition: background 0.2s, transform 0.05s;
      text-align: left;
      display: flex;
      align-items: center;
      border: 1px solid;
    }

    .option:active {
      transform: scale(0.99);
    }

    .question-mark {
      position: absolute;
      font-size: 1.8rem;
      font-weight: 900;
      opacity: 0.7;
      animation: float 1s infinite alternate;
      pointer-events: none;
      z-index: 10;
    }

    @keyframes float {
      from { transform: translateY(0); }
      to { transform: translateY(-8px); }
    }

    .placeholder-space {
      margin-top: 20px;
      padding: 12px;
      border: 2px dashed;
      border-radius: 24px;
      text-align: center;
      font-size: 0.95rem;
    }

    .black-mask {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: black;
      z-index: 2000;
      display: flex;
      justify-content: center;
      align-items: center;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
    }

    .black-mask.active {
      opacity: 1;
      pointer-events: auto;
    }

    .black-mask .dialog-white-text p {
      color: #ffffff;
      font-size: 1.8rem;
      font-weight: 600;
    }

    .dialog-white-text {
      background: transparent;
      box-shadow: none;
      border: none;
    }

    .dialog-white-text p {
      color: #ffffff;
      background: transparent;
      font-size: 1.6rem;
      font-weight: 600;
      margin-bottom: 30px;
      text-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
    }

    .white-mask {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: #ffffff;
      z-index: 2000;
      display: flex;
      justify-content: center;
      align-items: center;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
    }

    .white-mask.active {
      opacity: 1;
      pointer-events: auto;
    }

    .white-mask .dialog-black-text p {
      color: #000000;
      font-size: 2rem;
      font-weight: 700;
      letter-spacing: 2px;
    }

    .dialog-black-text {
      background: transparent;
      box-shadow: none;
      border: none;
    }

    .snow-mask {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: #000;
      z-index: 2000;
      display: flex;
      justify-content: center;
      align-items: center;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.6s ease;
      overflow: hidden;
    }

    .snow-mask.active {
      opacity: 1;
      pointer-events: auto;
    }

    .snow-canvas {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      image-rendering: pixelated;
    }

    .door-box {
      width: 200px;
      height: 260px;
      margin: 40px auto 30px;
      background: var(--door-border);
      position: relative;
      border-radius: 100px 100px 0 0;
      transition: background 0.4s;
      cursor: pointer;
    }

    .door-box::before {
      content: '';
      position: absolute;
      top: 8px;
      left: 8px;
      right: 8px;
      bottom: 0;
      background: var(--door-fill);
      border-radius: 92px 92px 0 0;
      transition: background 0.4s;
    }

    .blocks-overlay {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: transparent;
      z-index: 1500;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      align-content: center;
      gap: 0;
      padding: 0;
      opacity: 1;
      pointer-events: none;
      transition: opacity 0.5s ease;
      overflow: hidden;
    }

    .blocks-overlay.active {
      opacity: 1;
      pointer-events: auto;
    }

    .blocks-overlay.leaving {
      opacity: 0;
    }

    .blocks-overlay .block {
      color: #000000;
      line-height: 1;
      animation: blockAppear 0.1s forwards, blockTremble 0.18s infinite;
      opacity: 0;
      flex-shrink: 0;
    }

    @keyframes blockAppear {
      to { opacity: 1; }
    }

    @keyframes blockTremble {
      0%   { transform: translate(0, 0); }
      25%  { transform: translate(-1px, 1px); }
      50%  { transform: translate(1px, -1px); }
      75%  { transform: translate(-0.5px, -0.5px); }
      100% { transform: translate(0, 0); }
    }

    .end-container {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      flex: 1;
      text-align: center;
      padding: 40px 20px;
    }

    .end-title {
      font-size: 2.4rem;
      font-weight: 800;
      margin-bottom: 24px;
      letter-spacing: 2px;
    }

    .end-sub {
      font-size: 1.15rem;
      line-height: 1.8;
      margin-bottom: 48px;
    }

    .end-buttons {
      display: flex;
      flex-direction: column;
      gap: 16px;
      width: 100%;
      max-width: 280px;
    }

    .end-buttons .btn {
      margin: 0;
      max-width: none;
    }

    .hidden {
      display: none !important;
    }

    /* 黑色方块（■■）作为可点击 token，无任何视觉高亮提示 */
    .black-square-token {
      display: inline;
      /* 无 cursor 指针，无颜色变化，无过渡，纯文本外观 */
    }

    /* 小弹窗（关闭还是打开？） */
    .mini-dialog-overlay {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(0, 0, 0, 0.6);
      z-index: 2500;
      display: flex;
      justify-content: center;
      align-items: center;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.25s ease;
      padding: 20px;
    }

    .mini-dialog-overlay.active {
      opacity: 1;
      pointer-events: auto;
    }

    .mini-dialog {
      background: var(--dialog-bg);
      border: 1px solid var(--dialog-border);
      border-radius: 24px;
      padding: 24px 28px;
      max-width: 280px;
      width: 100%;
      text-align: center;
      box-shadow: 0 16px 40px rgba(0, 0, 0, 0.35);
      animation: miniPop 0.2s ease-out;
    }

    @keyframes miniPop {
      from { transform: scale(0.9); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }

    .mini-dialog p {
      font-size: 1.2rem;
      font-weight: 600;
      color: var(--text-primary);
      letter-spacing: 1px;
      margin: 0;
    }

    @media (max-width: 400px) {
      .hero-title { font-size: 2.2rem; }
      .btn { padding: 14px 22px; }
      .door-box { width: 160px; height: 210px; border-radius: 80px 80px 0 0; }
      .door-box::before { border-radius: 72px 72px 0 0; top: 6px; left: 6px; right: 6px; }
      .end-title { font-size: 2rem; }
    }
  </style>
</head>
<body>
  <div class="app" id="app">
    <div class="page active" id="page-home">
      <div class="hero-title">作业滞销<br>帮帮我们！</div>
      <div class="hero-sub">· 救救孩子 ·</div>
      <div style="flex:1;"></div>
      <button class="btn" id="btn-start">开始测试</button>
      <div style="height: 20px;"></div>
    </div>

    <div class="page" id="page-intro">
      <div class="intro-text">
        我重生了，重生在研究性学习作业未完成的那一天……<br>
        呸呸呸！总之只是一名苦命高中生完成作业的无奈之举，然后希望大家认真答题！感谢！
      </div>
      <div style="flex:1;"></div>
      <button class="btn" id="btn-intro-confirm">确定</button>
      <div style="height: 20px;"></div>
    </div>

    <div class="page" id="page-test">
      <div class="progress-container" id="progressContainer">
        <div class="progress-track">
          <div class="progress-fill" id="progressFill"></div>
        </div>
        <div class="progress-text" id="progressText">1 / 8</div>
      </div>

      <div id="question-container"></div>
      <div class="placeholder-space" id="placeholder" style="display:none;">⏳ 后续题目将在这里补充</div>
    </div>

    <div class="page" id="page-end">
      <div class="end-container">
        <div class="end-title">感谢您的参与</div>
        <div class="end-sub">可以的话请推荐给更多人哦～o(^▽^)o</div>
        <div class="end-buttons">
          <button class="btn" id="btn-restart">重来一次</button>
          <button class="btn btn-outline" id="btn-share">分享</button>
        </div>
      </div>
    </div>
  </div>

  <div class="overlay" id="overlay"></div>

  <div class="black-mask" id="blackMask">
    <div class="dialog-white-text" id="blackMaskContent"></div>
  </div>

  <div class="white-mask" id="whiteMask">
    <div class="dialog-black-text" id="whiteMaskContent"></div>
  </div>

  <div class="snow-mask" id="snowMask">
    <canvas class="snow-canvas" id="snowCanvas"></canvas>
  </div>

  <div class="blocks-overlay" id="blocksOverlay"></div>

  <div class="mini-dialog-overlay" id="miniDialogOverlay">
    <div class="mini-dialog">
      <p>关闭还是打开？</p>
    </div>
  </div>

  <script>
    (function() {
      let currentPage = 'home';
      let isDarkMode = false;
      let currentStep = 0;
      let totalSteps = 8;

      const app = document.getElementById('app');
      const pageHome = document.getElementById('page-home');
      const pageIntro = document.getElementById('page-intro');
      const pageTest = document.getElementById('page-test');
      const pageEnd = document.getElementById('page-end');
      const overlay = document.getElementById('overlay');
      const blackMask = document.getElementById('blackMask');
      const blackMaskContent = document.getElementById('blackMaskContent');
      const whiteMask = document.getElementById('whiteMask');
      const whiteMaskContent = document.getElementById('whiteMaskContent');
      const snowMask = document.getElementById('snowMask');
      const snowCanvas = document.getElementById('snowCanvas');
      const blocksOverlay = document.getElementById('blocksOverlay');
      const miniDialogOverlay = document.getElementById('miniDialogOverlay');
      const questionContainer = document.getElementById('question-container');
      const placeholder = document.getElementById('placeholder');
      const progressContainer = document.getElementById('progressContainer');
      const progressFill = document.getElementById('progressFill');
      const progressText = document.getElementById('progressText');

      const btnStart = document.getElementById('btn-start');
      const btnIntroConfirm = document.getElementById('btn-intro-confirm');
      const btnRestart = document.getElementById('btn-restart');
      const btnShare = document.getElementById('btn-share');

      let snowAnimationId = null;
      let snowCanvasCtx = null;
      let snowImgData = null;

      function setActivePage(pageId) {
        pageHome.classList.remove('active');
        pageIntro.classList.remove('active');
        pageTest.classList.remove('active');
        pageEnd.classList.remove('active');
        if (pageId === 'home') pageHome.classList.add('active');
        else if (pageId === 'intro') pageIntro.classList.add('active');
        else if (pageId === 'test') pageTest.classList.add('active');
        else if (pageId === 'end') pageEnd.classList.add('active');
        currentPage = pageId;
      }

      function updateProgress(step, total) {
        currentStep = step;
        totalSteps = total;
        let displayStep = step;
        if (step > total) displayStep = total;
        const percent = total > 0 ? (displayStep / total) * 100 : 0;
        progressFill.style.width = percent + '%';
        if (Number.isInteger(displayStep)) {
          progressText.textContent = displayStep + ' / ' + total;
        } else {
          progressText.textContent = displayStep.toFixed(1) + ' / ' + total;
        }
        progressContainer.classList.add('active');
      }

      function hideProgress() {
        progressContainer.classList.remove('active');
      }

      function resetProgress() {
        currentStep = 0;
        totalSteps = 8;
        progressFill.style.width = '0%';
        progressText.textContent = '0 / 8';
        progressContainer.classList.remove('active');
      }

      function hideOverlay() {
        overlay.classList.remove('active');
        overlay.innerHTML = '';
      }

      function showSimpleDialog(text, btnText, callback) {
        overlay.innerHTML = `
          <div class="dialog">
            <p>${text}</p>
            <button class="btn btn-small" id="simple-dialog-btn">${btnText || '确定'}</button>
          </div>
        `;
        overlay.classList.add('active');
        const btn = document.getElementById('simple-dialog-btn');
        if (btn) {
          btn.addEventListener('click', () => {
            if (callback) callback();
          });
        }
      }

      function showBlackMask(text, duration, callback) {
        if (text) {
          blackMaskContent.innerHTML = `<div class="dialog dialog-white-text" style="background:transparent;"><p>${text}</p></div>`;
        } else {
          blackMaskContent.innerHTML = '';
        }
        blackMask.classList.add('active');
        if (window._blackMaskTimer) clearTimeout(window._blackMaskTimer);
        if (duration && typeof duration === 'number') {
          window._blackMaskTimer = setTimeout(() => {
            hideBlackMask();
            if (callback) callback();
          }, duration);
        }
      }

      function hideBlackMask() {
        blackMask.classList.remove('active');
        blackMaskContent.innerHTML = '';
        if (window._blackMaskTimer) {
          clearTimeout(window._blackMaskTimer);
          window._blackMaskTimer = null;
        }
      }

      function showWhiteMask(text, duration, callback) {
        if (text) {
          whiteMaskContent.innerHTML = `<div class="dialog dialog-black-text" style="background:transparent;"><p>${text}</p></div>`;
        } else {
          whiteMaskContent.innerHTML = '';
        }
        whiteMask.classList.add('active');
        if (window._whiteMaskTimer) clearTimeout(window._whiteMaskTimer);
        if (duration && typeof duration === 'number') {
          window._whiteMaskTimer = setTimeout(() => {
            hideWhiteMask();
            if (callback) callback();
          }, duration);
        }
      }

      function hideWhiteMask() {
        whiteMask.classList.remove('active');
        whiteMaskContent.innerHTML = '';
        if (window._whiteMaskTimer) {
          clearTimeout(window._whiteMaskTimer);
          window._whiteMaskTimer = null;
        }
      }

      function startSnow(onStartFadeout) {
        if (snowAnimationId) cancelAnimationFrame(snowAnimationId);
        if (window._snowTimer) clearTimeout(window._snowTimer);

        snowMask.classList.add('active');
        snowCanvas.width = window.innerWidth;
        snowCanvas.height = window.innerHeight;
        snowCanvasCtx = snowCanvas.getContext('2d');
        snowImgData = snowCanvasCtx.createImageData(snowCanvas.width, snowCanvas.height);

        function renderSnow() {
          const data = snowImgData.data;
          const len = data.length;
          for (let i = 0; i < len; i += 4) {
            const v = Math.floor(Math.random() * 256);
            data[i] = v;
            data[i+1] = v;
            data[i+2] = v;
            data[i+3] = 255;
          }
          snowCanvasCtx.putImageData(snowImgData, 0, 0);
          snowAnimationId = requestAnimationFrame(renderSnow);
        }
        renderSnow();

        window._snowTimer = setTimeout(() => {
          if (onStartFadeout) onStartFadeout();
          snowMask.classList.remove('active');
          setTimeout(() => {
            stopSnowInternal();
          }, 650);
        }, 3000);
      }

      function stopSnowInternal() {
        if (snowAnimationId) {
          cancelAnimationFrame(snowAnimationId);
          snowAnimationId = null;
        }
        snowMask.classList.remove('active');
        if (window._snowTimer) {
          clearTimeout(window._snowTimer);
          window._snowTimer = null;
        }
      }

      function stopSnow() {
        stopSnowInternal();
      }

      function showBlocksToBlack(duration, onStartFadeout) {
        blocksOverlay.innerHTML = '';
        blocksOverlay.classList.remove('leaving');
        blocksOverlay.classList.add('active');

        const blockSize = 24;
        const viewportWidth = window.innerWidth;
        const viewportHeight = window.innerHeight;
        const cols = Math.ceil(viewportWidth / blockSize) + 1;
        const rows = Math.ceil(viewportHeight / blockSize) + 1;
        const totalBlocks = cols * rows;

        const fragment = document.createDocumentFragment();
        for (let i = 0; i < totalBlocks; i++) {
          const span = document.createElement('span');
          span.className = 'block';
          span.textContent = '■';
          span.style.fontSize = blockSize + 'px';
          span.style.width = blockSize + 'px';
          span.style.height = blockSize + 'px';
          span.style.display = 'inline-flex';
          span.style.justifyContent = 'center';
          span.style.alignItems = 'center';
          span.style.opacity = '0';
          span.style.animationDelay = (i * 0.0015) + 's, ' + (Math.random() * 0.18) + 's';
          fragment.appendChild(span);
        }
        blocksOverlay.appendChild(fragment);

        if (window._blocksTimer) clearTimeout(window._blocksTimer);
        window._blocksTimer = setTimeout(() => {
          if (onStartFadeout) onStartFadeout();
          blocksOverlay.classList.add('leaving');
          setTimeout(() => {
            blocksOverlay.classList.remove('active');
            blocksOverlay.classList.remove('leaving');
            blocksOverlay.innerHTML = '';
          }, 550);
        }, duration);
      }

      function hideBlocks() {
        blocksOverlay.classList.remove('active');
        blocksOverlay.classList.remove('leaving');
        blocksOverlay.innerHTML = '';
        if (window._blocksTimer) {
          clearTimeout(window._blocksTimer);
          window._blocksTimer = null;
        }
      }

      function showQuestionMarks() {
        document.querySelectorAll('.question-mark').forEach(el => el.remove());
        const positions = [
          { top: '20%', right: '8%' },
          { top: '35%', right: '5%' },
          { top: '50%', left: '4%' },
          { top: '65%', right: '7%' },
          { top: '80%', left: '6%' },
        ];
        positions.forEach((pos, i) => {
          const span = document.createElement('span');
          span.className = 'question-mark';
          span.textContent = '?';
          span.style.top = pos.top;
          if (pos.left) span.style.left = pos.left;
          if (pos.right) span.style.right = pos.right;
          span.style.animationDelay = (i * 0.15) + 's';
          app.appendChild(span);
        });
        setTimeout(() => {
          document.querySelectorAll('.question-mark').forEach(el => el.remove());
        }, 5000);
      }

      function clearQuestionMarks() {
        document.querySelectorAll('.question-mark').forEach(el => el.remove());
      }

      function setDarkMode(on) {
        if (on) {
          app.classList.add('dark-mode');
          document.body.classList.add('dark-mode');
          isDarkMode = true;
        } else {
          app.classList.remove('dark-mode');
          document.body.classList.remove('dark-mode');
          isDarkMode = false;
        }
      }

      function hideMiniDialog() {
        miniDialogOverlay.classList.remove('active');
        if (window._miniDialogTimer) {
          clearTimeout(window._miniDialogTimer);
          window._miniDialogTimer = null;
        }
      }

      function resetApp() {
        setDarkMode(false);
        hideOverlay();
        hideBlackMask();
        hideWhiteMask();
        stopSnow();
        hideBlocks();
        hideMiniDialog();
        clearQuestionMarks();
        questionContainer.innerHTML = '';
        placeholder.style.display = 'none';
        isDarkMode = false;
        resetProgress();
        window._changeClickCount = 0;
        window._changeTriggered = false;
        window._doorClickCount = 0;
        window._doorTriggered = false;
        window._squareClickCount = 0;
        window._squareTriggered = false;
      }

      function goToHome() {
        resetApp();
        setActivePage('home');
      }

      function goToEnd() {
        resetApp();
        hideProgress();
        setActivePage('end');
      }

      function renderQuestion(title, options, onSelect) {
        let html = `<div class="question-header">${title}</div><div class="options">`;
        options.forEach((opt, i) => {
          html += `<div class="option" data-index="${i}">${opt}</div>`;
        });
        html += `</div>`;
        questionContainer.innerHTML = html;
        placeholder.style.display = 'none';

        document.querySelectorAll('#question-container .option').forEach(el => {
          el.addEventListener('click', () => {
            if (el.classList.contains('selected')) return;
            document.querySelectorAll('#question-container .option').forEach(o => o.classList.remove('selected'));
            el.classList.add('selected');
            const index = parseInt(el.dataset.index, 10);
            onSelect(index, options[index]);
          });
        });
      }

      function renderQ1() {
        updateProgress(1, totalSteps);
        renderQuestion('你的性别是：', ['女', '男', '我不知道'], (index) => {
          if (index === 2) showQuestionMarks();
          setTimeout(() => renderQ2(), 300);
        });
      }

      function renderQ2() {
        updateProgress(2, totalSteps);
        renderQuestion('你的年龄在：', ['18岁以下', '18～28岁', '28～40岁', '40～60岁', '60岁以上', '受精卵阶段'], (index) => {
          if (index === 5) {
            showBlackMask('……年龄过小无法作答', 5000, () => {
              hideBlackMask();
              goToHome();
            });
          } else {
            setTimeout(() => renderQ3(), 300);
          }
        });
      }

      function renderQ3() {
        updateProgress(3, totalSteps);
        renderQuestion('过去一周里，你的心情如何？', ['非常好', '还可以', '一般', '不太好', '很糟糕', '我无法描述'], (index) => {
          if (index === 0 || index === 1) {
            showSimpleDialog('真好啊。', '确定', () => {
              hideOverlay();
              setTimeout(() => renderQ4(), 200);
            });
          } else if (index === 2) {
            showSimpleDialog('还可以。', '确定', () => {
              hideOverlay();
              setTimeout(() => renderQ4(), 200);
            });
          } else {
            overlay.innerHTML = `
              <div class="dialog">
                <p>……我会帮你的。</p>
                <button class="btn btn-small" id="btn-help-ack">确定</button>
              </div>
            `;
            overlay.classList.add('active');
            const ackBtn = document.getElementById('btn-help-ack');
            const timeoutId = setTimeout(() => {
              hideOverlay();
              showBlackMask('', 2000, () => {
                hideBlackMask();
                setTimeout(() => renderQ4(), 200);
              });
            }, 9000);
            ackBtn.addEventListener('click', () => {
              clearTimeout(timeoutId);
              hideOverlay();
              setTimeout(() => renderQ4(), 200);
            });
          }
        });
      }

      function renderQ4() {
        updateProgress(4, totalSteps);
        renderQuestion('过去几天，你有没有“突然回忆起某些事”的情况？', ['经常发生', '偶尔发生', '很少发生', '从不发生'], (index) => {
          if (index === 2 || index === 3) {
            totalSteps = 5;
            updateProgress(5, totalSteps);
            setTimeout(() => renderQ5Short(), 300);
          } else {
            totalSteps = 8;
            updateProgress(5, totalSteps);
            setTimeout(() => renderQ5Long(), 300);
          }
        });
      }

      function renderQ5Short() {
        updateProgress(5, totalSteps);
        renderQuestion('感谢你的参与！', ['继续'], (index) => {
          setTimeout(() => goToEnd(), 300);
        });
      }

      function renderQ5Long() {
        updateProgress(5, totalSteps);
        renderQuestion('是怎样的事呢？', ['很高兴的事', '不记得了', '很痛苦的事'], (index) => {
          if (index === 0) {
            totalSteps = 6;
            updateProgress(6, totalSteps);
            setTimeout(() => renderQ5Short(), 300);
          } else if (index === 1) {
            showSimpleDialog('忘记是件……', '确定', () => {
              hideOverlay();
              totalSteps = 8;
              updateProgress(6, totalSteps);
              setTimeout(() => renderQ6(), 300);
            });
          } else {
            showBlocksToBlack(5000, () => {
              totalSteps = 8;
              updateProgress(6, totalSteps);
              renderQ6();
            });
          }
        });
      }

      function renderQ6() {
        updateProgress(6, totalSteps);
        const title = '你想<span class="change-highlight" id="changeWord">改变</span>这个结果吗？';
        renderQuestion(title, ['想', '不想'], (index) => {
          if (index === 0) {
            setDarkMode(true);
            overlay.innerHTML = `
              <div class="dialog" style="background:#0a0c0f; border-color:#272d34;">
                <p style="color:#e8ecf0;">……好的。</p>
              </div>
            `;
            overlay.classList.add('active');
            setTimeout(() => {
              hideOverlay();
              totalSteps = 8;
              updateProgress(7, totalSteps);
              setTimeout(() => renderQ7(), 300);
            }, 3000);
          } else {
            overlay.innerHTML = `
              <div class="dialog">
                <p>……好的。</p>
              </div>
            `;
            overlay.classList.add('active');
            setTimeout(() => {
              hideOverlay();
              totalSteps = 8;
              updateProgress(7, totalSteps);
              setTimeout(() => renderQ7(), 300);
            }, 3000);
          }
        });

        const changeWord = document.getElementById('changeWord');
        if (changeWord) {
          window._changeClickCount = 0;
          window._changeTriggered = false;

          changeWord.addEventListener('click', (e) => {
            if (window._changeTriggered) return;
            e.stopPropagation();

            window._changeClickCount = (window._changeClickCount || 0) + 1;

            if (window._changeClickCount >= 5) {
              window._changeTriggered = true;
              showWelcomeOverlay(() => {
                changeWord.classList.add('stopped');
              });
            }
          });
        }
      }

      function showWelcomeOverlay(callback) {
        const welcomeOverlay = document.createElement('div');
        welcomeOverlay.style.cssText = `
          position: fixed;
          top: 0; left: 0; width: 100%; height: 100%;
          background: #000000;
          z-index: 3000;
          display: flex;
          justify-content: center;
          align-items: center;
          flex-wrap: wrap;
          align-content: center;
          gap: 2px;
          padding: 10px;
          overflow: hidden;
          opacity: 0;
          transition: opacity 0.3s ease;
          pointer-events: auto;
        `;

        const text = '欢迎';
        const redColor = '#ff3b3b';
        const totalChars = 600;
        const fragment = document.createDocumentFragment();
        for (let i = 0; i < totalChars; i++) {
          const span = document.createElement('span');
          span.textContent = text;
          span.style.cssText = `
            color: ${redColor};
            font-size: ${20 + Math.random() * 30}px;
            font-weight: 900;
            line-height: 1;
            display: inline-block;
            transform: rotate(${(Math.random() - 0.5) * 20}deg);
            opacity: ${0.7 + Math.random() * 0.3};
            flex-shrink: 0;
          `;
          fragment.appendChild(span);
        }
        welcomeOverlay.appendChild(fragment);
        document.body.appendChild(welcomeOverlay);

        requestAnimationFrame(() => {
          welcomeOverlay.style.opacity = '1';
        });

        setTimeout(() => {
          welcomeOverlay.style.opacity = '0';
          setTimeout(() => {
            if (welcomeOverlay.parentNode) {
              welcomeOverlay.parentNode.removeChild(welcomeOverlay);
            }
            if (callback) callback();
          }, 350);
        }, 3000);
      }

      function renderQ7() {
        updateProgress(7, totalSteps);
        renderQuestion('如果现在你的面前有一扇门，你会打开它吗？', ['我会立即打开它', '我会先想想', '我不会打开它'], (index) => {
          if (index === 2) {
            totalSteps = 8;
            updateProgress(8, totalSteps);
            setTimeout(() => goToEnd(), 300);
          } else if (index === 1) {
            showSimpleDialog('……谨慎是件好事。', '确定', () => {
              hideOverlay();
              totalSteps = 8;
              updateProgress(8, totalSteps);
              setTimeout(() => goToEnd(), 300);
            });
          } else {
            showSimpleDialog('打开它吧。', '确定', () => {
              hideOverlay();
              updateProgress(7.5, totalSteps);
              setTimeout(() => renderQ75(), 300);
            });
          }
        });
      }

      function renderQ75() {
        updateProgress(7.5, totalSteps);
        let html = `<div class="door-box" id="doorBox"></div>`;
        html += `<div class="options">`;
        html += `<div class="option" data-index="0">打开</div>`;
        html += `<div class="option" data-index="1">打开</div>`;
        html += `</div>`;
        questionContainer.innerHTML = html;
        placeholder.style.display = 'none';

        const doorBox = document.getElementById('doorBox');
        if (doorBox) {
          window._doorClickCount = 0;
          window._doorTriggered = false;

          doorBox.addEventListener('click', (e) => {
            e.stopPropagation();
            if (window._doorTriggered) return;

            window._doorClickCount = (window._doorClickCount || 0) + 1;

            if (window._doorClickCount >= 3) {
              window._doorTriggered = true;
              showTypewriterDialog();
            }
          });
        }

        document.querySelectorAll('#question-container .option').forEach(el => {
          el.addEventListener('click', () => {
            if (el.classList.contains('selected')) return;
            document.querySelectorAll('#question-container .option').forEach(o => o.classList.remove('selected'));
            el.classList.add('selected');
            startSnow(() => {
              totalSteps = 8;
              updateProgress(8, totalSteps);
              renderQuestion('感谢你的参与！', ['继续'], (idx) => {
                setTimeout(() => goToEnd(), 300);
              });
            });
          });
        });
      }

      function showTypewriterDialog() {
        overlay.innerHTML = `
          <div class="dialog typewriter-dialog" style="background:#0a0c0f; border-color:#272d34;">
            <p id="typewriterText" style="color:#e8ecf0; min-height:180px;"></p>
            <button class="btn btn-small btn-white" id="typewriterContinue" style="display:none;">继续</button>
          </div>
        `;
        overlay.classList.add('active');

        const textEl = document.getElementById('typewriterText');
        const continueBtn = document.getElementById('typewriterContinue');
        const lines = [
          '……你找到这里了。',
          '如你所见，这是一个demo。如你所见，这里有一扇门。',
          '记住它，然后，等待着，■■它。',
          '再见了。'
        ];
        const fullText = lines.join('\n');
        let charIndex = 0;

        function typeChar() {
          if (charIndex < fullText.length) {
            textEl.textContent = fullText.substring(0, charIndex + 1);
            charIndex++;
            setTimeout(typeChar, 45 + Math.random() * 30);
          } else {
            continueBtn.style.display = 'block';
            // 打字结束后，处理“■■”的点击（无高亮）
            bindSquareClick();
          }
        }
        typeChar();

        continueBtn.addEventListener('click', () => {
          hideOverlay();
        });
      }

      // 在打字结束后，将文本中的“■■”替换为可点击的包裹元素，但无任何视觉提示
      function bindSquareClick() {
        const textEl = document.getElementById('typewriterText');
        if (!textEl) return;
        const rawText = textEl.textContent;
        // 查找“■■”在全文中的位置，替换为带 class 的 span
        const target = '■■';
        const index = rawText.indexOf(target);
        if (index === -1) return;
        const before = rawText.substring(0, index);
        const after = rawText.substring(index + target.length);
        textEl.innerHTML = '';
        textEl.appendChild(document.createTextNode(before));
        const token = document.createElement('span');
        token.className = 'black-square-token';
        token.textContent = target;
        textEl.appendChild(token);
        textEl.appendChild(document.createTextNode(after));

        window._squareClickCount = 0;
        window._squareTriggered = false;

        token.addEventListener('click', (e) => {
          e.stopPropagation();
          if (window._squareTriggered) return;

          window._squareClickCount = (window._squareClickCount || 0) + 1;

          if (window._squareClickCount >= 2) {
            window._squareTriggered = true;
            showMiniDialog();
          }
        });
      }

      // 小弹窗：关闭还是打开？约3秒后自动消失
      function showMiniDialog() {
        miniDialogOverlay.classList.add('active');
        if (window._miniDialogTimer) clearTimeout(window._miniDialogTimer);
        window._miniDialogTimer = setTimeout(() => {
          miniDialogOverlay.classList.remove('active');
          window._miniDialogTimer = null;
        }, 3000);
      }

      btnRestart.addEventListener('click', () => {
        resetApp();
        setActivePage('home');
      });

      btnShare.addEventListener('click', () => {
        const shareData = {
          title: '作业滞销帮帮我们！',
          text: '来帮帮这个苦命高中生完成研究性学习作业吧！',
          url: window.location.href,
        };

        if (navigator.share) {
          navigator.share(shareData).catch((err) => {
            console.log('分享取消或失败:', err);
          });
        } else if (navigator.clipboard && navigator.clipboard.writeText) {
          navigator.clipboard.writeText(window.location.href).then(() => {
            showSimpleDialog('链接已复制到剪贴板！', '好的', () => {
              hideOverlay();
            });
          }).catch(() => {
            fallbackCopy();
          });
        } else {
          fallbackCopy();
        }

        function fallbackCopy() {
          const textarea = document.createElement('textarea');
          textarea.value = window.location.href;
          textarea.style.position = 'fixed';
          textarea.style.opacity = '0';
          document.body.appendChild(textarea);
          textarea.select();
          try {
            document.execCommand('copy');
            showSimpleDialog('链接已复制到剪贴板！', '好的', () => {
              hideOverlay();
            });
          } catch (e) {
            showSimpleDialog('复制失败，请手动分享链接：\n' + window.location.href, '好的', () => {
              hideOverlay();
            });
          }
          document.body.removeChild(textarea);
        }
      });

      btnStart.addEventListener('click', () => {
        setActivePage('intro');
      });

      btnIntroConfirm.addEventListener('click', () => {
        overlay.innerHTML = `
          <div class="dialog" style="background: #0a0c0f; border: 1px solid #272d34;">
            <p style="color: #e8ecf0; font-size: 1.6rem; font-weight: 600;">……你真的想好了吗？</p>
            <button class="btn btn-white" id="btn-final-confirm" style="background:#fbfcfd; color:#1a1d21;">确定</button>
          </div>
        `;
        overlay.classList.add('active');
        document.getElementById('btn-final-confirm').addEventListener('click', () => {
          hideOverlay();
          showBlackMask('', 600, () => {
            hideBlackMask();
            setActivePage('test');
            resetApp();
            totalSteps = 8;
            renderQ1();
          });
        });
      });

      setActivePage('home');
      placeholder.style.display = 'none';
      hideProgress();
      window._changeClickCount = 0;
      window._changeTriggered = false;
      window._doorClickCount = 0;
      window._doorTriggered = false;
      window._squareClickCount = 0;
      window._squareTriggered = false;
    })();
  </script>
</body>
</html>
