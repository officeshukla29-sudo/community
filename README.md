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
.nav-user span.profile-name-btn { cursor: pointer; font-weight: 600; color: var(--indigo-dark); }
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

/* People / friends / inbox */
.people-panel { display: flex; flex-direction: column; gap: 20px; }
.people-search-form { display: flex; gap: 8px; }
.people-search-form input { flex: 1; border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; font-size: 14px; outline: none; }
.people-search-form button { border: none; background: var(--indigo); color: #fff; border-radius: 8px; padding: 10px 16px; font-size: 13px; font-weight: 600; }
.people-section h3 { font-family: 'Fraunces', serif; font-size: 16px; margin: 0 0 10px; color: var(--indigo-dark); }
.person-card { display: flex; align-items: center; gap: 12px; background: var(--card); border: 1px solid var(--border); border-radius: 10px; padding: 10px 12px; margin-bottom: 8px; }
.person-card .avatar { background: var(--sage); }
.person-info { flex: 1; min-width: 0; }
.person-name { font-weight: 600; font-size: 14px; }
.person-email { font-size: 12px; color: var(--ink-soft); overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
.person-action { display: flex; gap: 6px; flex-shrink: 0; }
.person-action button { border: 1px solid var(--border); background: var(--paper); border-radius: 7px; padding: 6px 12px; font-size: 12px; font-weight: 600; }
.person-action .add-friend-btn, .person-action .accept-btn, .person-action .open-thread-btn, .person-action .message-friend-btn { background: var(--indigo); color: #fff; border: none; }
.person-action .decline-btn { color: var(--danger); border-color: var(--danger); }
.person-status { font-size: 12px; color: var(--ink-soft); font-weight: 600; }

.chat-thread-header { display: flex; align-items: center; gap: 10px; padding: 12px 16px; border-bottom: 1px solid var(--border); }
.chat-thread-header button { background: none; border: none; color: var(--indigo); font-weight: 600; font-size: 13px; padding: 0; }
.chat-thread-header span { font-weight: 600; font-size: 14px; }

/* Profile modal */
.modal-overlay { position: fixed; inset: 0; background: rgba(28,28,30,0.45); display: flex; align-items: center; justify-content: center; z-index: 1000; padding: 16px; }
.modal-box { width: 100%; max-width: 380px; background: var(--card); border-radius: 14px; padding: 28px; box-shadow: 0 20px 40px -20px rgba(28,28,30,0.3); }
.modal-actions { display: flex; gap: 8px; justify-content: flex-end; margin-top: 4px; }
.modal-cancel-btn { border: 1px solid var(--border); background: var(--paper); border-radius: 8px; padding: 11px 16px; font-size: 14px; }

.section-header-row { display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; }
.section-header-row h3 { margin: 0; }
.small-action-btn { border: none; background: var(--indigo); color: #fff; border-radius: 7px; padding: 7px 12px; font-size: 12px; font-weight: 600; }
.group-checklist { max-height: 220px; overflow-y: auto; border: 1px solid var(--border); border-radius: 8px; padding: 8px; display: flex; flex-direction: column; gap: 6px; }
.checklist-item { display: flex; align-items: center; gap: 8px; font-size: 14px; padding: 4px 2px; }
.checklist-item input { width: 16px; height: 16px; }
</style>
</head>
<body>

<div id="root"></div>

<script>
/* ============================================================
   CONFIG — persisted API URL for the Apps Script backend
   ============================================================ */
/* ============================================================
   Visible error banner — so mobile users can see JS errors
   without needing devtools/console access
   ============================================================ */
window.addEventListener('error', (e) => showFatalError(e.message));
window.addEventListener('unhandledrejection', (e) => showFatalError(e.reason?.message || String(e.reason)));

function showFatalError(message) {
  let banner = document.getElementById('fatal-error-banner');
  if (!banner) {
    banner = document.createElement('div');
    banner.id = 'fatal-error-banner';
    banner.style.cssText = 'position:fixed;top:0;left:0;right:0;background:#B5473F;color:#fff;padding:12px 16px;font-size:13px;z-index:9999;font-family:sans-serif;';
    document.body.prepend(banner);
  }
  banner.textContent = 'Error: ' + message;
}

const CONFIG_KEY = 'nexus_api_url';
const USER_KEY = 'nexus_community_user';
const DEFAULT_API_URL = 'https://script.google.com/macros/s/AKfycbxbI2l7s8erxJlKYHnYL-syBI5v4ZRo1v_CEWhhFlIoqsi8hUWFr9L842AdfIYlaTJ9pA/exec';
// Always sync to DEFAULT_API_URL — overwrites any stale URL saved from a previous version of this file
const previousApiUrl = localStorage.getItem(CONFIG_KEY);
if (previousApiUrl && previousApiUrl !== DEFAULT_API_URL) {
  localStorage.removeItem(USER_KEY); // old session belongs to a different sheet's user list
}
let API_URL = DEFAULT_API_URL;
localStorage.setItem(CONFIG_KEY, API_URL);
let currentUser = null;
try { currentUser = JSON.parse(localStorage.getItem(USER_KEY) || 'null'); } catch { currentUser = null; }

let currentTab = 'feed';
let feedPosts = [];
let feedHasMore = true;
let feedInterval = null;

// Generalized conversation state — used for both the community room ("general")
// and 1:1 DM threads (conversationId = dm_<sortedUserIds>)
let activeConversationId = 'general';
let activeConversationTitle = null; // null = community chat; else the friend's name (DM)
let conversationMessages = [];
let conversationLastTimestamp = null;
let conversationInterval = null;

let recordingKind = null; // null | 'audio' | 'video'
let mediaRecorder = null;
let recordedChunks = [];
let activeStream = null;

const openComments = {}; // postId -> bool
const commentsCache = {}; // postId -> array

// People / friends / inbox state
let suggestedPeople = [];
let friendRequests = [];
let friendsList = [];
let selectedFriend = null; // { userId, name } — set when a DM thread is open in the Inbox tab

/* ============================================================
   API helper
   ============================================================ */
async function apiCall(action, payload = {}) {
  if (!API_URL) throw new Error('No API URL configured');
  const controller = new AbortController();
  const timeoutId = setTimeout(() => controller.abort(), 15000);
  let res;
  try {
    res = await fetch(API_URL, {
      method: 'POST',
      headers: { 'Content-Type': 'text/plain;charset=utf-8' },
      body: JSON.stringify({ action, ...payload }),
      signal: controller.signal,
    });
  } catch (err) {
    if (err.name === 'AbortError') {
      throw new Error('Request timed out after 15s — check your internet connection.');
    }
    throw new Error('Network error: ' + err.message);
  } finally {
    clearTimeout(timeoutId);
  }
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

function dmId(userIdA, userIdB) {
  return 'dm_' + [userIdA, userIdB].sort().join('_');
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

  stopFeedPolling();
  stopConversationPolling();

  if (currentTab === 'feed') { renderFeedPanel(); startFeedPolling(); }
  else if (currentTab === 'chat') { enterConversation('general', null); }
  else if (currentTab === 'people') { renderPeoplePanel(); }
  else if (currentTab === 'inbox') { renderInboxPanel(); }
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
          <button id="tab-people" class="${currentTab === 'people' ? 'active' : ''}">People</button>
          <button id="tab-inbox" class="${currentTab === 'inbox' ? 'active' : ''}">Inbox</button>
        </div>
      </div>
      <div class="nav-user">
        <span id="profile-open-btn" class="profile-name-btn">${escapeHtml(currentUser.name)}</span>
        <button id="logout-btn">Log out</button>
      </div>
    </nav>
    <main class="main ${currentTab === 'chat' || currentTab === 'inbox' ? 'main-chat' : ''}" id="main-panel"></main>
  </div>`;
}

function attachShellHandlers() {
  document.getElementById('tab-feed').addEventListener('click', () => { currentTab = 'feed'; render(); });
  document.getElementById('tab-chat').addEventListener('click', () => { currentTab = 'chat'; render(); });
  document.getElementById('tab-people').addEventListener('click', () => { currentTab = 'people'; render(); });
  document.getElementById('tab-inbox').addEventListener('click', () => { currentTab = 'inbox'; render(); });
  document.getElementById('profile-open-btn').addEventListener('click', openProfileModal);
  document.getElementById('logout-btn').addEventListener('click', () => {
    localStorage.removeItem(USER_KEY);
    currentUser = null;
    stopFeedPolling(); stopConversationPolling();
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
   Chat (generalized — powers both the community room and DMs)
   ============================================================ */
async function loadConversationInitial() {
  const res = await apiCall('getMessages', { conversationId: activeConversationId });
  conversationMessages = res.messages;
  conversationLastTimestamp = conversationMessages.length
    ? conversationMessages[conversationMessages.length - 1].createdAt
    : null;
  renderChatPanel();
}

async function pollConversation() {
  const res = await apiCall('getMessages', { conversationId: activeConversationId, since: conversationLastTimestamp });
  if (res.messages.length) {
    conversationMessages = conversationMessages.concat(res.messages);
    conversationLastTimestamp = res.messages[res.messages.length - 1].createdAt;
    renderChatPanel();
  }
}

function enterConversation(conversationId, title) {
  activeConversationId = conversationId;
  activeConversationTitle = title || null;
  conversationMessages = [];
  conversationLastTimestamp = null;
  stopConversationPolling();
  loadConversationInitial();
  conversationInterval = setInterval(pollConversation, 4000);
}

function stopConversationPolling() { if (conversationInterval) { clearInterval(conversationInterval); conversationInterval = null; } }

function exitToInboxList() {
  stopConversationPolling();
  selectedFriend = null;
  renderInboxPanel();
}

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
  const isDm = !!activeConversationTitle;
  const headerHtml = isDm ? `
    <div class="chat-thread-header">
      <button id="chat-back-btn">← Back</button>
      <span>${escapeHtml(activeConversationTitle)}</span>
    </div>` : '';
  const placeholder = isDm ? `Message ${escapeHtml(activeConversationTitle)}…` : 'Message the community…';

  panel.innerHTML = `
    <div class="chat">
      ${headerHtml}
      <div class="chat-messages" id="chat-messages">
        ${conversationMessages.map(chatBubbleHtml).join('')}
      </div>
      <div id="recording-area"></div>
      <form class="chat-input-row" id="chat-form">
        <button type="button" id="rec-audio-btn" title="Record audio">🎤</button>
        <button type="button" id="rec-video-btn" title="Record video">🎥</button>
        <input id="chat-text" placeholder="${placeholder}" />
        <button type="submit">Send</button>
      </form>
    </div>`;
  const msgBox = document.getElementById('chat-messages');
  msgBox.scrollTop = msgBox.scrollHeight;
  if (isDm) document.getElementById('chat-back-btn').addEventListener('click', exitToInboxList);
  attachChatHandlers();
}

function attachChatHandlers() {
  document.getElementById('chat-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const input = document.getElementById('chat-text');
    const text = input.value.trim();
    if (!text) return;
    input.value = '';
    const res = await apiCall('sendMessage', { conversationId: activeConversationId, senderId: currentUser.userId, senderName: currentUser.name, type: 'text', text });
    conversationMessages.push(res.message);
    conversationLastTimestamp = res.message.createdAt;
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
      conversationId: activeConversationId, senderId: currentUser.userId, senderName: currentUser.name,
      type: kind, mediaBase64: base64, mediaMime: blob.type, mediaName: `${kind}-${Date.now()}.webm`,
    });
    conversationMessages.push(res.message);
    conversationLastTimestamp = res.message.createdAt;
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
   People — search, friend requests, people you may know
   ============================================================ */
function personCardHtml(user, actionHtml) {
  return `
  <div class="person-card">
    <div class="avatar">${escapeHtml((user.name || '?')[0] || '?').toUpperCase()}</div>
    <div class="person-info">
      <div class="person-name">${escapeHtml(user.name)}</div>
      <div class="person-email">${escapeHtml(user.email)}</div>
    </div>
    <div class="person-action">${actionHtml}</div>
  </div>`;
}

function friendStatusActionHtml(user) {
  if (user.friendStatus === 'accepted') return `<span class="person-status">Friends</span>`;
  if (user.friendStatus === 'pending_sent') return `<span class="person-status">Requested</span>`;
  if (user.friendStatus === 'pending_received') return `<span class="person-status">Check requests ↓</span>`;
  return `<button class="add-friend-btn" data-user-id="${user.userId}">Add friend</button>`;
}

function renderPeoplePanel() {
  const panel = document.getElementById('main-panel');
  panel.innerHTML = `
    <div class="people-panel">
      <form class="people-search-form" id="people-search-form">
        <input id="people-search-input" placeholder="Search people by name or email…" />
        <button type="submit">Search</button>
      </form>
      <div id="people-search-results"></div>

      <section class="people-section">
        <h3>Friend requests</h3>
        <div id="people-requests"><p class="post-time">Loading…</p></div>
      </section>

      <section class="people-section">
        <h3>People you may know</h3>
        <div id="people-suggested"><p class="post-time">Loading…</p></div>
      </section>

      <section class="people-section">
        <h3>My friends</h3>
        <div id="people-friends"><p class="post-time">Loading…</p></div>
      </section>
    </div>`;

  document.getElementById('people-search-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const query = document.getElementById('people-search-input').value.trim();
    const box = document.getElementById('people-search-results');
    if (!query) { box.innerHTML = ''; return; }
    box.innerHTML = '<p class="post-time">Searching…</p>';
    const res = await apiCall('searchUsers', { query, currentUserId: currentUser.userId });
    box.innerHTML = res.users.length
      ? `<div class="people-section"><h3>Search results</h3>${res.users.map(u => personCardHtml(u, friendStatusActionHtml(u))).join('')}</div>`
      : '<p class="empty-state">No matches.</p>';
    attachPeopleActionHandlers();
  });

  refreshPeopleData();
}

async function refreshPeopleData() {
  const [suggestedRes, requestsRes, friendsRes] = await Promise.all([
    apiCall('getPeopleYouMayKnow', { userId: currentUser.userId, limit: 10 }),
    apiCall('getFriendRequests', { userId: currentUser.userId }),
    apiCall('getFriends', { userId: currentUser.userId }),
  ]);
  suggestedPeople = suggestedRes.users;
  friendRequests = requestsRes.requests;
  friendsList = friendsRes.friends;

  const reqBox = document.getElementById('people-requests');
  const sugBox = document.getElementById('people-suggested');
  const frBox = document.getElementById('people-friends');
  if (!reqBox) return; // panel no longer visible (tab switched away)

  reqBox.innerHTML = friendRequests.length
    ? friendRequests.map(r => personCardHtml(r.from, `
        <button class="accept-btn" data-friendship-id="${r.friendshipId}">Accept</button>
        <button class="decline-btn" data-friendship-id="${r.friendshipId}">Decline</button>`)).join('')
    : '<p class="empty-state">No pending requests.</p>';

  sugBox.innerHTML = suggestedPeople.length
    ? suggestedPeople.map(u => personCardHtml(u, `<button class="add-friend-btn" data-user-id="${u.userId}">Add friend</button>`)).join('')
    : '<p class="empty-state">No suggestions right now.</p>';

  frBox.innerHTML = friendsList.length
    ? friendsList.map(u => personCardHtml(u, `<button class="message-friend-btn" data-user-id="${u.userId}" data-user-name="${escapeHtml(u.name)}">Message</button>`)).join('')
    : '<p class="empty-state">No friends yet — send some requests above.</p>';

  attachPeopleActionHandlers();
}

function attachPeopleActionHandlers() {
  document.querySelectorAll('.add-friend-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      btn.disabled = true; btn.textContent = 'Sending…';
      try {
        await apiCall('sendFriendRequest', { fromUserId: currentUser.userId, fromName: currentUser.name, toUserId: btn.dataset.userId });
        refreshPeopleData();
      } catch (err) {
        alert(err.message);
        btn.disabled = false; btn.textContent = 'Add friend';
      }
    });
  });

  document.querySelectorAll('.accept-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      await apiCall('respondFriendRequest', { friendshipId: btn.dataset.friendshipId, accept: true });
      refreshPeopleData();
    });
  });

  document.querySelectorAll('.decline-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      await apiCall('respondFriendRequest', { friendshipId: btn.dataset.friendshipId, accept: false });
      refreshPeopleData();
    });
  });

  document.querySelectorAll('.message-friend-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      selectedFriend = { userId: btn.dataset.userId, name: btn.dataset.userName };
      currentTab = 'inbox';
      render();
    });
  });
}

/* ============================================================
   Inbox — direct messages + groups, opens a thread (reuses chat panel)
   ============================================================ */
function renderInboxPanel() {
  if (selectedFriend) {
    const convoId = selectedFriend.isGroup ? 'group_' + selectedFriend.userId : dmId(currentUser.userId, selectedFriend.userId);
    enterConversation(convoId, selectedFriend.name);
    return;
  }
  loadInboxLists();
}

async function loadInboxLists() {
  const panel = document.getElementById('main-panel');
  panel.innerHTML = `
    <div class="people-panel">
      <section class="people-section">
        <div class="section-header-row">
          <h3>Groups</h3>
          <button id="new-group-btn" class="small-action-btn">+ New group</button>
        </div>
        <div id="inbox-groups"><p class="post-time">Loading…</p></div>
      </section>
      <section class="people-section">
        <h3>Direct messages</h3>
        <div id="inbox-friend-list"><p class="post-time">Loading…</p></div>
      </section>
    </div>`;

  document.getElementById('new-group-btn').addEventListener('click', openNewGroupModal);

  const [groupsRes, friendsRes] = await Promise.all([
    apiCall('getMyGroups', { userId: currentUser.userId }),
    apiCall('getFriends', { userId: currentUser.userId }),
  ]);

  const groupsBox = document.getElementById('inbox-groups');
  if (groupsBox) {
    groupsBox.innerHTML = groupsRes.groups.length
      ? groupsRes.groups.map(g => personCardHtml(
          { name: g.name, email: g.memberIds.length + ' members' },
          `<button class="open-group-btn" data-group-id="${g.groupId}" data-group-name="${escapeHtml(g.name)}">Open</button>`
        )).join('')
      : '<p class="empty-state">No groups yet — create one above.</p>';
    document.querySelectorAll('.open-group-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        selectedFriend = { userId: btn.dataset.groupId, name: btn.dataset.groupName, isGroup: true };
        renderInboxPanel();
      });
    });
  }

  const friendBox = document.getElementById('inbox-friend-list');
  if (friendBox) {
    friendBox.innerHTML = friendsRes.friends.length
      ? friendsRes.friends.map(u => personCardHtml(u, `<button class="open-thread-btn" data-user-id="${u.userId}" data-user-name="${escapeHtml(u.name)}">Open</button>`)).join('')
      : '<p class="empty-state">Add friends in the People tab to start messaging.</p>';
    document.querySelectorAll('.open-thread-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        selectedFriend = { userId: btn.dataset.userId, name: btn.dataset.userName };
        renderInboxPanel();
      });
    });
  }
}

async function openNewGroupModal() {
  const existing = document.getElementById('group-modal-overlay');
  if (existing) existing.remove();

  const overlay = document.createElement('div');
  overlay.id = 'group-modal-overlay';
  overlay.className = 'modal-overlay';
  overlay.innerHTML = `
    <div class="modal-box">
      <h3 class="card-title" style="font-size:22px;">New group</h3>
      <form class="card-form" id="group-form">
        <input id="group-name" placeholder="Group name" required />
        <div id="group-friend-checklist" class="group-checklist"><p class="post-time">Loading friends…</p></div>
        <p class="form-error hidden" id="group-error"></p>
        <div class="modal-actions">
          <button type="button" class="modal-cancel-btn" id="group-cancel-btn">Cancel</button>
          <button type="submit" class="btn-primary" id="group-save-btn" style="margin-top:0;">Create</button>
        </div>
      </form>
    </div>`;
  document.body.appendChild(overlay);
  overlay.addEventListener('click', (e) => { if (e.target === overlay) overlay.remove(); });
  document.getElementById('group-cancel-btn').addEventListener('click', () => overlay.remove());

  const res = await apiCall('getFriends', { userId: currentUser.userId });
  const listBox = document.getElementById('group-friend-checklist');
  if (!listBox) return; // modal closed before friends loaded
  listBox.innerHTML = res.friends.length
    ? res.friends.map(u => `
        <label class="checklist-item">
          <input type="checkbox" value="${u.userId}" />
          <span>${escapeHtml(u.name)}</span>
        </label>`).join('')
    : '<p class="empty-state">Add some friends first before creating a group.</p>';

  document.getElementById('group-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const errorEl = document.getElementById('group-error');
    const saveBtn = document.getElementById('group-save-btn');
    errorEl.classList.add('hidden');

    const name = document.getElementById('group-name').value.trim();
    const memberIds = [...listBox.querySelectorAll('input[type=checkbox]:checked')].map(cb => cb.value);
    if (!memberIds.length) {
      errorEl.textContent = 'Pick at least one friend.';
      errorEl.classList.remove('hidden');
      return;
    }

    saveBtn.disabled = true; saveBtn.textContent = 'Creating…';
    try {
      const res = await apiCall('createGroup', { name, memberIds, createdBy: currentUser.userId });
      overlay.remove();
      selectedFriend = { userId: res.group.groupId, name: res.group.name, isGroup: true };
      renderInboxPanel();
    } catch (err) {
      errorEl.textContent = err.message;
      errorEl.classList.remove('hidden');
      saveBtn.disabled = false; saveBtn.textContent = 'Create';
    }
  });
}

/* ============================================================
   Profile modal — edit name / bio / photo
   ============================================================ */
function openProfileModal() {
  const existing = document.getElementById('profile-modal-overlay');
  if (existing) existing.remove();

  const overlay = document.createElement('div');
  overlay.id = 'profile-modal-overlay';
  overlay.className = 'modal-overlay';
  overlay.innerHTML = `
    <div class="modal-box">
      <h3 class="card-title" style="font-size:22px;">Edit profile</h3>
      <form class="card-form" id="profile-form">
        <input id="profile-name" value="${escapeHtml(currentUser.name)}" placeholder="Name" required />
        <textarea id="profile-bio" placeholder="Bio" rows="3">${escapeHtml(currentUser.bio || '')}</textarea>
        <label class="file-btn">
          <span id="profile-photo-label">Change photo</span>
          <input type="file" id="profile-photo-input" accept="image/*" hidden />
        </label>
        <p class="form-error hidden" id="profile-error"></p>
        <div class="modal-actions">
          <button type="button" class="modal-cancel-btn" id="profile-cancel-btn">Cancel</button>
          <button type="submit" class="btn-primary" id="profile-save-btn" style="margin-top:0;">Save</button>
        </div>
      </form>
    </div>`;
  document.body.appendChild(overlay);

  overlay.addEventListener('click', (e) => { if (e.target === overlay) overlay.remove(); });
  document.getElementById('profile-cancel-btn').addEventListener('click', () => overlay.remove());

  const photoInput = document.getElementById('profile-photo-input');
  photoInput.addEventListener('change', () => {
    document.getElementById('profile-photo-label').textContent = photoInput.files[0] ? photoInput.files[0].name : 'Change photo';
  });

  document.getElementById('profile-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const errorEl = document.getElementById('profile-error');
    const saveBtn = document.getElementById('profile-save-btn');
    errorEl.classList.add('hidden');
    saveBtn.disabled = true; saveBtn.textContent = 'Saving…';
    try {
      const name = document.getElementById('profile-name').value.trim();
      const bio = document.getElementById('profile-bio').value.trim();
      const file = photoInput.files[0] || null;
      let photoBase64 = null;
      if (file) photoBase64 = await fileToBase64(file);
      const res = await apiCall('updateProfile', {
        userId: currentUser.userId, name, bio,
        photoBase64, photoMime: file?.type, photoName: file?.name,
      });
      currentUser = res.user;
      localStorage.setItem(USER_KEY, JSON.stringify(currentUser));
      overlay.remove();
      render();
    } catch (err) {
      errorEl.textContent = err.message;
      errorEl.classList.remove('hidden');
      saveBtn.disabled = false; saveBtn.textContent = 'Save';
    }
  });
}

/* ============================================================
   Boot
   ============================================================ */
render();
</script>
</body>
</html>
