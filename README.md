<!doctype html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Community</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:wght@400;600;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  --ink: #1C1C1E;
  --ink-soft: #5B5B5E;
  --paper: #F1F0EC;
  --card: #FFFFFF;
  --border: #E2E0D8;
  --indigo: #3D4B8C;
  --indigo-dark: #2C3868;
  --sage: #6B8068;
  --danger: #B5473F;
}
* { box-sizing: border-box; }
html, body { margin: 0; padding: 0; }
body { font-family: 'Inter', -apple-system, sans-serif; background: var(--paper); color: var(--ink); -webkit-font-smoothing: antialiased; }
button { font-family: inherit; cursor: pointer; }
input, textarea { font-family: inherit; }

/* Setup / auth screens */
.screen { min-height: 100vh; display: flex; align-items: center; justify-content: center;
  background: radial-gradient(circle at 20% 20%, rgba(61,75,140,0.08), transparent 40%),
              radial-gradient(circle at 80% 80%, rgba(107,128,104,0.10), transparent 40%), var(--paper); }
.card-box { width: 100%; max-width: 380px; background: var(--card); border: 1px solid var(--border); border-radius: 14px;
  padding: 40px 32px; box-shadow: 0 20px 40px -20px rgba(28,28,30,0.15); }
.card-title { font-family: 'Fraunces', serif; font-weight: 700; font-size: 28px; margin: 0 0 4px; color: var(--indigo-dark); }
.card-subtitle { margin: 0 0 22px; color: var(--ink-soft); font-size: 14px; line-height: 1.5; }
.card-form { display: flex; flex-direction: column; gap: 10px; }
.card-form input, .card-form textarea { padding: 11px 13px; border-radius: 8px; border: 1px solid var(--border); font-size: 14px; outline: none; }
.card-form input:focus, .card-form textarea:focus { border-color: var(--indigo); }
.btn-primary { padding: 11px 13px; border-radius: 8px; border: none; font-size: 14px; font-weight: 600; background: var(--indigo); color: #fff; margin-top: 6px; }
.btn-primary:disabled { opacity: .6; }
.form-error { color: var(--danger); font-size: 13px; margin: 0; }
.switch-line { margin-top: 18px; font-size: 13px; color: var(--ink-soft); text-align: center; }
.link-btn { background: none; border: none; color: var(--indigo); font-weight: 600; padding: 0; font-size: 13px; }

/* App shell */
.app { min-height: 100vh; }
.navbar { display: flex; align-items: center; justify-content: space-between; padding: 14px 28px; background: var(--card);
  border-bottom: 1px solid var(--border); position: sticky; top: 0; z-index: 10; }
.nav-left { display: flex; align-items: center; gap: 20px; }
.brand { font-family: 'Fraunces', serif; font-weight: 700; font-size: 20px; color: var(--indigo-dark); }
.nav-tabs { display: flex; gap: 6px; }
.nav-tabs button { background: none; border: none; border-radius: 7px; padding: 6px 14px; font-size: 13px; color: var(--ink-soft); font-weight: 600; }
.nav-tabs button.active { background: var(--indigo); color: #fff; }
.nav-user { display: flex; align-items: center; gap: 14px; font-size: 14px; color: var(--ink-soft); }
.nav-user button { background: none; border: 1px solid var(--border); border-radius: 7px; padding: 6px 12px; font-size: 13px; color: var(--ink); }
.main { max-width: 560px; margin: 0 auto; padding: 28px 16px 80px; }
.main-chat { max-width: 640px; padding: 20px 16px; height: calc(100vh - 130px); display: flex; flex-direction: column; }

/* Feed */
.feed { display: flex; flex-direction: column; gap: 16px; }
.empty-state { text-align: center; color: var(--ink-soft); padding: 40px 0; font-size: 14px; }
.create-post { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 16px; }
.create-post textarea { width: 100%; border: none; resize: none; outline: none; font-size: 15px; }
.create-post-row { display: flex; align-items: center; justify-content: space-between; margin-top: 10px; padding-top: 10px; border-top: 1px solid var(--border); }
.file-btn { font-size: 13px; color: var(--ink-soft); cursor: pointer; }
.create-post-row button[type='submit'] { background: var(--indigo); color: #fff; border: none; border-radius: 7px; padding: 8px 18px; font-weight: 600; font-size: 13px; }
.create-post-row button[type='submit']:disabled { opacity: .5; }
.post-card { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 16px; }
.post-header { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; }
.avatar { width: 36px; height: 36px; border-radius: 50%; background: var(--sage); color: #fff; display: flex; align-items: center;
  justify-content: center; font-weight: 700; font-size: 14px; flex-shrink: 0; }
.post-author { font-weight: 600; font-size: 14px; }
.post-time { font-size: 12px; color: var(--ink-soft); }
.post-text { font-size: 15px; line-height: 1.5; margin: 0 0 10px; white-space: pre-wrap; }
.post-image { width: 100%; border-radius: 8px; margin-bottom: 10px; display: block; }
.post-actions { display: flex; gap: 10px; border-top: 1px solid var(--border); padding-top: 10px; }
.post-actions button { background: none; border: 1px solid var(--border); border-radius: 7px; padding: 6px 12px; font-size: 13px; color: var(--ink-soft); }
.post-actions button.liked { color: var(--danger); border-color: var(--danger); }
.comments { margin-top: 12px; padding-top: 12px; border-top: 1px solid var(--border); display: flex; flex-direction: column; gap: 8px; }
.comment { font-size: 13px; line-height: 1.4; }
.comment-author { font-weight: 600; }
.comment-form { display: flex; gap: 8px; margin-top: 4px; }
.comment-form input { flex: 1; border: 1px solid var(--border); border-radius: 7px; padding: 8px 10px; font-size: 13px; outline: none; }
.comment-form button { border: none; background: var(--sage); color: #fff; border-radius: 7px; padding: 8px 14px; font-size: 13px; font-weight: 600; }
.load-more { align-self: center; background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 9px 20px; font-size: 13px; color: var(--ink-soft); }

/* Chat */
.chat { display: flex; flex-direction: column; flex: 1; background: var(--card); border: 1px solid var(--border); border-radius: 12px; overflow: hidden; }
.chat-messages { flex: 1; overflow-y: auto; padding: 16px; display: flex; flex-direction: column; gap: 10px; }
.chat-bubble-row { display: flex; justify-content: flex-start; }
.chat-bubble-row.mine { justify-content: flex-end; }
.chat-bubble { max-width: 75%; background: var(--paper); border-radius: 12px; padding: 8px 12px; font-size: 14px; }
.chat-bubble-row.mine .chat-bubble { background: var(--indigo); color: #fff; }
.chat-bubble p { margin: 0; line-height: 1.4; }
.chat-sender { font-size: 11px; font-weight: 700; color: var(--sage); margin-bottom: 2px; }
.chat-bubble audio, .chat-bubble video { max-width: 100%; border-radius: 8px; }
.chat-bubble img { max-width: 100%; border-radius: 8px; display: block; }
.chat-input-row { display: flex; gap: 8px; padding: 12px; border-top: 1px solid var(--border); }
.chat-input-row input { flex: 1; border: 1px solid var(--border); border-radius: 8px; padding: 9px 12px; font-size: 14px; outline: none; }
.chat-input-row button { border: 1px solid var(--border); background: var(--paper); border-radius: 8px; padding: 8px 14px; font-size: 14px; }
.chat-input-row button[type='submit'] { background: var(--indigo); color: #fff; border: none; font-weight: 600; }
.recording-preview { padding: 16px; border-top: 1px solid var(--border); text-align: center; }
.recording-preview video { max-width: 100%; max-height: 260px; border-radius: 8px; background: #000; }
.recording-indicator { color: var(--danger); font-weight: 600; font-size: 14px; }
.recording-controls { display: flex; gap: 8px; justify-content: center; margin-top: 10px; }
.recording-controls button { border: 1px solid var(--border); background: var(--card); border-radius: 7px; padding: 8px 16px; font-size: 13px; }

.hidden { display: none !important; }
</style>
</head>
<body>

<div id="root"></div>

<script>
/* ============================================================
   CONFIG — persisted API URL for the Apps Script backend
   ============================================================ */
const CONFIG_KEY = 'nexus_api_url';
const USER_KEY = 'nexus_community_user';
const DEFAULT_API_URL = 'https://script.google.com/macros/s/AKfycbwaPWWg7XI3kDh2PL4FTd-BZ-NYmb8DbSWWAhjAwtD_mWnzziP-FSX1YxWgcNy8oBWs/exec';
let API_URL = localStorage.getItem(CONFIG_KEY) || DEFAULT_API_URL;
if (!localStorage.getItem(CONFIG_KEY)) localStorage.setItem(CONFIG_KEY, API_URL);
let currentUser = null;
try { currentUser = JSON.parse(localStorage.getItem(USER_KEY) || 'null'); } catch { currentUser = null; }

let currentTab = 'feed';
let feedPosts = [];
let feedHasMore = true;
let feedInterval = null;

let chatMessages = [];
let lastChatTimestamp = null;
let chatInterval = null;
let recordingKind = null; // null | 'audio' | 'video'
let mediaRecorder = null;
let recordedChunks = [];
let activeStream = null;

const openComments = {}; // postId -> bool
const commentsCache = {}; // postId -> array

/* ============================================================
   API helper
   ============================================================ */
async function apiCall(action, payload = {}) {
  if (!API_URL) throw new Error('No API URL configured');
  const res = await fetch(API_URL, {
    method: 'POST',
    headers: { 'Content-Type': 'text/plain;charset=utf-8' },
    body: JSON.stringify({ action, ...payload }),
  });
  const data = await res.json();
  if (!data.ok) throw new Error(data.error || 'Request failed');
  return data;
}

function fileToBase64(file) {
  return new Promise((resolve, reject) => {
    const reader = new FileReader();
    reader.onload = () => resolve(reader.result.split(',')[1]);
    reader.onerror = reject;
    reader.readAsDataURL(file);
  });
}

function blobToBase64(blob) {
  return new Promise((resolve, reject) => {
    const reader = new FileReader();
    reader.onload = () => resolve(reader.result.split(',')[1]);
    reader.onerror = reject;
    reader.readAsDataURL(blob);
  });
}

function escapeHtml(str) {
  return (str || '').replace(/[&<>"']/g, (c) => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
}

/* ============================================================
   Root render dispatcher
   ============================================================ */
function render() {
  const root = document.getElementById('root');
  if (!API_URL) { root.innerHTML = setupScreenHtml(); attachSetupHandlers(); return; }
  if (!currentUser) { root.innerHTML = authScreenHtml('login'); attachAuthHandlers('login'); return; }
  root.innerHTML = appShellHtml();
  attachShellHandlers();
  if (currentTab === 'feed') { renderFeedPanel(); startFeedPolling(); stopChatPolling(); }
  else { renderChatPanel(); startChatPolling(); stopFeedPolling(); }
}

/* ============================================================
   Setup screen — first run, ask for the Apps Script URL
   ============================================================ */
function setupScreenHtml() {
  return `
  <div class="screen">
    <div class="card-box">
      <h1 class="card-title">Community</h1>
      <p class="card-subtitle">Paste your Apps Script Web app URL to connect this app to your Google Sheet database.</p>
      <form class="card-form" id="setup-form">
        <input type="text" id="setup-url" placeholder="https://script.google.com/macros/s/.../exec" required />
        <p class="form-error hidden" id="setup-error"></p>
        <button class="btn-primary" type="submit" id="setup-submit">Connect</button>
      </form>
    </div>
  </div>`;
}

function attachSetupHandlers() {
  document.getElementById('setup-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const errorEl = document.getElementById('setup-error');
    const submitBtn = document.getElementById('setup-submit');
    errorEl.classList.add('hidden');

    let url = document.getElementById('setup-url').value.trim();
    // strip any stray whitespace/newlines from mobile copy-paste
    url = url.replace(/\s+/g, '');
    if (!url) return;
    if (!/^https:\/\/script\.google\.com\/macros\/s\/.+\/exec$/.test(url)) {
      errorEl.textContent = 'That doesn\'t look like an Apps Script /exec URL. Copy it from Deploy > Manage deployments.';
      errorEl.classList.remove('hidden');
      return;
    }

    submitBtn.disabled = true;
    submitBtn.textContent = 'Connecting…';
    try {
      const testRes = await fetch(url, {
        method: 'POST',
        headers: { 'Content-Type': 'text/plain;charset=utf-8' },
        body: JSON.stringify({ action: 'getPosts', offset: 0, limit: 1 }),
      });
      const data = await testRes.json();
      if (data.ok === undefined) throw new Error('Unexpected response from the script.');
      // ok:false with "Unknown action" would mean something is very wrong;
      // ok:true or a normal getPosts error both mean the endpoint is reachable.
      API_URL = url;
      localStorage.setItem(CONFIG_KEY, url);
      render();
    } catch (err) {
      errorEl.textContent = 'Could not connect: ' + err.message + '. Check that the deployment access is set to "Anyone" and that you copied the /exec URL (not /dev).';
      errorEl.classList.remove('hidden');
      submitBtn.disabled = false;
      submitBtn.textContent = 'Connect';
    }
  });
}

/* ============================================================
   Auth screen — login / signup
   ============================================================ */
function authScreenHtml(mode) {
  return `
  <div class="screen">
    <div class="card-box">
      <h1 class="card-title">Community</h1>
      <p class="card-subtitle">${mode === 'login' ? 'Welcome back.' : 'Create your account.'}</p>
      <form class="card-form" id="auth-form">
        ${mode === 'signup' ? `<input type="text" id="auth-name" placeholder="Full name" required />` : ''}
        <input type="email" id="auth-email" placeholder="Email" required />
        <input type="password" id="auth-password" placeholder="Password" minlength="6" required />
        <p class="form-error hidden" id="auth-error"></p>
        <button class="btn-primary" type="submit" id="auth-submit">${mode === 'login' ? 'Log in' : 'Sign up'}</button>
      </form>
      <p class="switch-line">
        ${mode === 'login' ? "Don't have an account?" : 'Already have an account?'}
        <button class="link-btn" id="auth-switch">${mode === 'login' ? 'Sign up' : 'Log in'}</button>
      </p>
    </div>
  </div>`;
}

function attachAuthHandlers(mode) {
  document.getElementById('auth-switch').addEventListener('click', () => {
    const root = document.getElementById('root');
    const next = mode === 'login' ? 'signup' : 'login';
    root.innerHTML = authScreenHtml(next);
    attachAuthHandlers(next);
  });

  document.getElementById('auth-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const errorEl = document.getElementById('auth-error');
    const submitBtn = document.getElementById('auth-submit');
    errorEl.classList.add('hidden');
    submitBtn.disabled = true;
    submitBtn.textContent = 'Please wait…';
    try {
      const email = document.getElementById('auth-email').value.trim();
      const password = document.getElementById('auth-password').value;
      let result;
      if (mode === 'login') {
        result = await apiCall('login', { email, password });
      } else {
        const name = document.getElementById('auth-name').value.trim();
        result = await apiCall('signup', { name, email, password });
      }
      currentUser = result.user;
      localStorage.setItem(USER_KEY, JSON.stringify(currentUser));
      render();
    } catch (err) {
      errorEl.textContent = err.message;
      errorEl.classList.remove('hidden');
      submitBtn.disabled = false;
      submitBtn.textContent = mode === 'login' ? 'Log in' : 'Sign up';
    }
  });
}

/* ============================================================
   App shell — navbar + tab switcher
   ============================================================ */
function appShellHtml() {
  return `
  <div class="app">
    <nav class="navbar">
      <div class="nav-left">
        <span class="brand">Community</span>
        <div class="nav-tabs">
          <button id="tab-feed" class="${currentTab === 'feed' ? 'active' : ''}">Feed</button>
          <button id="tab-chat" class="${currentTab === 'chat' ? 'active' : ''}">Chat</button>
        </div>
      </div>
      <div class="nav-user">
        <span>${escapeHtml(currentUser.name)}</span>
        <button id="logout-btn">Log out</button>
      </div>
    </nav>
    <main class="main ${currentTab === 'chat' ? 'main-chat' : ''}" id="main-panel"></main>
  </div>`;
}

function attachShellHandlers() {
  document.getElementById('tab-feed').addEventListener('click', () => { currentTab = 'feed'; render(); });
  document.getElementById('tab-chat').addEventListener('click', () => { currentTab = 'chat'; render(); });
  document.getElementById('logout-btn').addEventListener('click', () => {
    localStorage.removeItem(USER_KEY);
    currentUser = null;
    stopFeedPolling(); stopChatPolling();
    render();
  });
}

/* ============================================================
   Feed
   ============================================================ */
async function loadFirstPage() {
  const res = await apiCall('getPosts', { offset: 0, limit: 10 });
  feedPosts = res.posts;
  feedHasMore = res.hasMore;
  renderFeedPanel();
}

async function loadMorePosts() {
  const res = await apiCall('getPosts', { offset: feedPosts.length, limit: 10 });
  feedPosts = feedPosts.concat(res.posts);
  feedHasMore = res.hasMore;
  renderFeedPanel();
}

function startFeedPolling() {
  if (feedInterval) return;
  loadFirstPage();
  feedInterval = setInterval(loadFirstPage, 15000);
}
function stopFeedPolling() { if (feedInterval) { clearInterval(feedInterval); feedInterval = null; } }

function postCardHtml(post) {
  const liked = openComments[post.postId + '_liked'] === true;
  const comments = commentsCache[post.postId] || [];
  const showComments = !!openComments[post.postId];
  return `
  <article class="post-card" data-post-id="${post.postId}">
    <header class="post-header">
      <div class="avatar">${escapeHtml((post.authorName || '?')[0] || '?').toUpperCase()}</div>
      <div>
        <div class="post-author">${escapeHtml(post.authorName)}</div>
        <div class="post-time">${post.createdAt ? new Date(post.createdAt).toLocaleString() : 'just now'}</div>
      </div>
    </header>
    ${post.text ? `<p class="post-text">${escapeHtml(post.text)}</p>` : ''}
    ${post.imageURL ? `<img class="post-image" src="${post.imageURL}" alt="" />` : ''}
    <div class="post-actions">
      <button class="like-btn ${liked ? 'liked' : ''}" data-post-id="${post.postId}">♥ <span class="like-count">${post.likeCount || 0}</span></button>
      <button class="comment-toggle-btn" data-post-id="${post.postId}">💬 ${post.commentCount ?? comments.length}</button>
    </div>
    <div class="comments ${showComments ? '' : 'hidden'}" data-comments-for="${post.postId}">
      ${comments.map(c => `<div class="comment"><span class="comment-author">${escapeHtml(c.authorName)}</span> ${escapeHtml(c.text)}</div>`).join('')}
      <form class="comment-form" data-post-id="${post.postId}">
        <input placeholder="Write a comment…" />
        <button type="submit">Send</button>
      </form>
    </div>
  </article>`;
}

function renderFeedPanel() {
  const panel = document.getElementById('main-panel');
  if (!panel) return;
  panel.innerHTML = `
    <div class="feed">
      <div class="create-post">
        <textarea id="new-post-text" placeholder="Share something with the community…" rows="3"></textarea>
        <div class="create-post-row">
          <label class="file-btn">
            <span id="new-post-filename">Add photo</span>
            <input type="file" id="new-post-image" accept="image/*" hidden />
          </label>
          <button type="button" id="new-post-submit">Post</button>
        </div>
      </div>
      ${feedPosts.length === 0 ? '<p class="empty-state">Nothing here yet — be the first to post.</p>' : ''}
      ${feedPosts.map(postCardHtml).join('')}
      ${feedHasMore ? '<button class="load-more" id="load-more-btn">Load more</button>' : ''}
    </div>`;
  attachFeedHandlers();
}

function attachFeedHandlers() {
  const imageInput = document.getElementById('new-post-image');
  imageInput.addEventListener('change', () => {
    document.getElementById('new-post-filename').textContent = imageInput.files[0] ? imageInput.files[0].name : 'Add photo';
  });

  document.getElementById('new-post-submit').addEventListener('click', async (e) => {
    const btn = e.target;
    const textEl = document.getElementById('new-post-text');
    const text = textEl.value.trim();
    const file = imageInput.files[0] || null;
    if (!text && !file) return;
    btn.disabled = true; btn.textContent = 'Posting…';
    try {
      let imageBase64 = null;
      if (file) imageBase64 = await fileToBase64(file);
      await apiCall('createPost', {
        authorId: currentUser.userId, authorName: currentUser.name,
        text, imageBase64, imageMime: file?.type, imageName: file?.name,
      });
      textEl.value = ''; imageInput.value = '';
      await loadFirstPage();
    } catch (err) {
      alert('Failed to post: ' + err.message);
    } finally {
      btn.disabled = false; btn.textContent = 'Post';
    }
  });

  const loadMoreBtn = document.getElementById('load-more-btn');
  if (loadMoreBtn) loadMoreBtn.addEventListener('click', async () => {
    loadMoreBtn.disabled = true; loadMoreBtn.textContent = 'Loading…';
    await loadMorePosts();
  });

  document.querySelectorAll('.like-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      const postId = btn.dataset.postId;
      const wasLiked = openComments[postId + '_liked'] === true;
      openComments[postId + '_liked'] = !wasLiked;
      const countEl = btn.querySelector('.like-count');
      countEl.textContent = Number(countEl.textContent) + (wasLiked ? -1 : 1);
      btn.classList.toggle('liked');
      try {
        const res = await apiCall('toggleLike', { postId, userId: currentUser.userId });
        openComments[postId + '_liked'] = res.liked;
        countEl.textContent = res.likeCount;
        btn.classList.toggle('liked', res.liked);
      } catch (err) { console.error(err); }
    });
  });

  document.querySelectorAll('.comment-toggle-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      const postId = btn.dataset.postId;
      const opening = !openComments[postId];
      openComments[postId] = opening;
      const container = document.querySelector(`[data-comments-for="${postId}"]`);
      container.classList.toggle('hidden', !opening);
      if (opening && !commentsCache[postId]) {
        const res = await apiCall('getComments', { postId });
        commentsCache[postId] = res.comments;
        renderCommentsInto(container, postId);
      }
    });
  });

  document.querySelectorAll('.comment-form').forEach(form => {
    form.addEventListener('submit', async (e) => {
      e.preventDefault();
      const postId = form.dataset.postId;
      const input = form.querySelector('input');
      const text = input.value.trim();
      if (!text) return;
      input.value = '';
      const res = await apiCall('addComment', { postId, authorId: currentUser.userId, authorName: currentUser.name, text });
      commentsCache[postId] = (commentsCache[postId] || []).concat([res.comment]);
      renderCommentsInto(form.parentElement, postId);
    });
  });
}

function renderCommentsInto(container, postId) {
  const comments = commentsCache[postId] || [];
  const formHtml = `<form class="comment-form" data-post-id="${postId}"><input placeholder="Write a comment…" /><button type="submit">Send</button></form>`;
  container.innerHTML = comments.map(c => `<div class="comment"><span class="comment-author">${escapeHtml(c.authorName)}</span> ${escapeHtml(c.text)}</div>`).join('') + formHtml;
  container.querySelector('.comment-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const input = e.target.querySelector('input');
    const text = input.value.trim();
    if (!text) return;
    input.value = '';
    const res = await apiCall('addComment', { postId, authorId: currentUser.userId, authorName: currentUser.name, text });
    commentsCache[postId] = (commentsCache[postId] || []).concat([res.comment]);
    renderCommentsInto(container, postId);
  });
}

/* ============================================================
   Chat
   ============================================================ */
async function loadChatInitial() {
  const res = await apiCall('getMessages', { conversationId: 'general' });
  chatMessages = res.messages;
  lastChatTimestamp = chatMessages.length ? chatMessages[chatMessages.length - 1].createdAt : null;
  renderChatPanel();
}

async function pollChat() {
  const res = await apiCall('getMessages', { conversationId: 'general', since: lastChatTimestamp });
  if (res.messages.length) {
    chatMessages = chatMessages.concat(res.messages);
    lastChatTimestamp = res.messages[res.messages.length - 1].createdAt;
    renderChatPanel();
  }
}

function startChatPolling() {
  if (chatInterval) return;
  loadChatInitial();
  chatInterval = setInterval(pollChat, 4000);
}
function stopChatPolling() { if (chatInterval) { clearInterval(chatInterval); chatInterval = null; } }

function chatBubbleHtml(m) {
  const mine = m.senderId === currentUser.userId;
  let mediaHtml = '';
  if (m.type === 'audio') mediaHtml = `<audio controls src="${m.mediaURL}"></audio>`;
  else if (m.type === 'video') mediaHtml = `<video controls src="${m.mediaURL}"></video>`;
  else if (m.type === 'image') mediaHtml = `<img src="${m.mediaURL}" alt="" />`;
  return `
  <div class="chat-bubble-row ${mine ? 'mine' : ''}">
    <div class="chat-bubble">
      ${!mine ? `<div class="chat-sender">${escapeHtml(m.senderName)}</div>` : ''}
      ${m.type === 'text' ? `<p>${escapeHtml(m.text)}</p>` : mediaHtml}
    </div>
  </div>`;
}

function renderChatPanel() {
  const panel = document.getElementById('main-panel');
  if (!panel) return;
  panel.innerHTML = `
    <div class="chat">
      <div class="chat-messages" id="chat-messages">
        ${chatMessages.map(chatBubbleHtml).join('')}
      </div>
      <div id="recording-area"></div>
      <form class="chat-input-row" id="chat-form">
        <button type="button" id="rec-audio-btn" title="Record audio">🎤</button>
        <button type="button" id="rec-video-btn" title="Record video">🎥</button>
        <input id="chat-text" placeholder="Message the community…" />
        <button type="submit">Send</button>
      </form>
    </div>`;
  const msgBox = document.getElementById('chat-messages');
  msgBox.scrollTop = msgBox.scrollHeight;
  attachChatHandlers();
}

function attachChatHandlers() {
  document.getElementById('chat-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const input = document.getElementById('chat-text');
    const text = input.value.trim();
    if (!text) return;
    input.value = '';
    const res = await apiCall('sendMessage', { conversationId: 'general', senderId: currentUser.userId, senderName: currentUser.name, type: 'text', text });
    chatMessages.push(res.message);
    lastChatTimestamp = res.message.createdAt;
    renderChatPanel();
  });

  document.getElementById('rec-audio-btn').addEventListener('click', () => startRecording('audio'));
  document.getElementById('rec-video-btn').addEventListener('click', () => startRecording('video'));
}

async function startRecording(kind) {
  try {
    const constraints = kind === 'video' ? { video: true, audio: true } : { audio: true };
    activeStream = await navigator.mediaDevices.getUserMedia(constraints);
  } catch (err) {
    alert('Could not access ' + (kind === 'video' ? 'camera/microphone' : 'microphone') + ': ' + err.message);
    return;
  }
  recordingKind = kind;
  recordedChunks = [];
  mediaRecorder = new MediaRecorder(activeStream);
  mediaRecorder.ondataavailable = (e) => recordedChunks.push(e.data);
  mediaRecorder.start();

  const area = document.getElementById('recording-area');
  document.getElementById('chat-form').classList.add('hidden');
  if (kind === 'video') {
    area.innerHTML = `
      <div class="recording-preview">
        <video id="rec-preview" autoplay muted playsinline></video>
        <div class="recording-controls">
          <button id="rec-stop">Stop and send</button>
          <button id="rec-cancel">Cancel</button>
        </div>
      </div>`;
    document.getElementById('rec-preview').srcObject = activeStream;
  } else {
    area.innerHTML = `
      <div class="recording-preview">
        <p class="recording-indicator">● Recording audio…</p>
        <div class="recording-controls">
          <button id="rec-stop">Stop and send</button>
          <button id="rec-cancel">Cancel</button>
        </div>
      </div>`;
  }
  document.getElementById('rec-stop').addEventListener('click', stopRecording);
  document.getElementById('rec-cancel').addEventListener('click', cancelRecording);
}

async function stopRecording() {
  const kind = recordingKind;
  const blob = await new Promise((resolve) => {
    mediaRecorder.onstop = () => resolve(new Blob(recordedChunks, { type: mediaRecorder.mimeType }));
    mediaRecorder.stop();
  });
  activeStream.getTracks().forEach(t => t.stop());
  recordingKind = null;
  document.getElementById('recording-area').innerHTML = '';
  document.getElementById('chat-form').classList.remove('hidden');

  try {
    const base64 = await blobToBase64(blob);
    const res = await apiCall('sendMessage', {
      conversationId: 'general', senderId: currentUser.userId, senderName: currentUser.name,
      type: kind, mediaBase64: base64, mediaMime: blob.type, mediaName: `${kind}-${Date.now()}.webm`,
    });
    chatMessages.push(res.message);
    lastChatTimestamp = res.message.createdAt;
    renderChatPanel();
  } catch (err) {
    alert('Failed to send: ' + err.message);
  }
}

function cancelRecording() {
  if (mediaRecorder) mediaRecorder.stop();
  if (activeStream) activeStream.getTracks().forEach(t => t.stop());
  recordingKind = null;
  document.getElementById('recording-area').innerHTML = '';
  document.getElementById('chat-form').classList.remove('hidden');
}

/* ============================================================
   Boot
   ============================================================ */
render();
</script>
</body>
</html>
