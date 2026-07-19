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
button { font-family: inherit; cursor: pointer; transition: background-color 0.15s ease, border-color 0.15s ease, color 0.15s ease, opacity 0.15s ease, transform 0.08s ease; }
button:active { transform: scale(0.96); }
input, textarea { transition: border-color 0.15s ease, box-shadow 0.15s ease; }
.post-card, .person-card, .chat-bubble, .story-circle, .reel-card { transition: box-shadow 0.2s ease, transform 0.15s ease; }
.post-card:hover, .person-card:hover { box-shadow: 0 6px 18px -10px rgba(28,28,30,0.18); }
.story-circle:hover { transform: translateY(-2px); }
.modal-overlay { animation: modal-fade-in 0.18s ease; }
.modal-box { animation: modal-pop-in 0.2s ease; }
@keyframes modal-fade-in { from { opacity: 0; } to { opacity: 1; } }
@keyframes modal-pop-in { from { opacity: 0; transform: scale(0.96) translateY(6px); } to { opacity: 1; transform: scale(1) translateY(0); } }
.chat-messages { scroll-behavior: smooth; }
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
.avatar-img { border-radius: 50%; object-fit: cover; flex-shrink: 0; }

.nav-user span.profile-name-btn { cursor: pointer; font-weight: 600; color: var(--indigo-dark); display: flex; align-items: center; gap: 8px; }

.comment { display: flex; align-items: flex-start; gap: 8px; font-size: 13px; line-height: 1.4; }
.comment > div { padding-top: 2px; }

.mention-dropdown { position: absolute; bottom: 100%; left: 0; margin-bottom: 4px; background: var(--card); border: 1px solid var(--border); border-radius: 8px; box-shadow: 0 8px 20px -8px rgba(28,28,30,0.25); z-index: 50; min-width: 160px; overflow: hidden; }
.mention-item { padding: 8px 12px; font-size: 13px; cursor: pointer; }
.mention-item:hover { background: var(--paper); }

.toast-notification { position: fixed; top: 16px; right: 16px; max-width: 300px; background: var(--card); border: 1px solid var(--border); border-left: 4px solid var(--indigo); border-radius: 10px; padding: 12px 14px; box-shadow: 0 12px 28px -12px rgba(28,28,30,0.3); z-index: 3000; cursor: pointer; font-size: 13px; animation: toast-in 0.2s ease-out; }
.toast-notification strong { display: block; margin-bottom: 3px; font-size: 13px; }
.toast-notification div { color: var(--ink-soft); font-size: 12px; }
@keyframes toast-in { from { transform: translateX(20px); opacity: 0; } to { transform: translateX(0); opacity: 1; } }
.nav-user button { background: none; border: 1px solid var(--border); border-radius: 7px; padding: 6px 12px; font-size: 13px; color: var(--ink); }
.main { max-width: 560px; margin: 0 auto; padding: 28px 16px 80px; }
.main-chat { max-width: 640px; padding: 20px 16px; height: calc(100vh - 130px); display: flex; flex-direction: column; }
.main-reels { max-width: 480px; padding: 0; height: calc(100vh - 61px); }

.reels-container { height: 100%; overflow-y: scroll; scroll-snap-type: y mandatory; background: #000; position: relative; }
.upload-reel-btn { position: sticky; top: 12px; left: 12px; z-index: 5; background: var(--indigo); color: #fff; border: none; border-radius: 20px; padding: 8px 16px; font-size: 13px; font-weight: 600; margin: 12px; }
.reel-card { scroll-snap-align: start; height: calc(100vh - 61px); position: relative; display: flex; align-items: center; justify-content: center; background: #000; }
.reel-video { width: 100%; height: 100%; object-fit: contain; }
.reel-overlay { position: absolute; bottom: 0; left: 0; right: 0; padding: 16px; background: linear-gradient(to top, rgba(0,0,0,0.7), transparent); color: #fff; display: flex; flex-direction: column; gap: 8px; }
.reel-author { display: flex; align-items: center; gap: 8px; font-size: 14px; font-weight: 600; }
.reel-caption { font-size: 13px; color: rgba(255,255,255,0.9); }
.reel-like-btn { align-self: flex-start; background: rgba(255,255,255,0.15); border: none; border-radius: 20px; padding: 6px 14px; color: #fff; font-size: 13px; }
.reel-like-btn.active { background: var(--danger); }
.load-more-reel-btn { display: block; margin: 16px auto; background: rgba(255,255,255,0.15); color: #fff; border: none; border-radius: 8px; padding: 10px 20px; }

/* Polls / quizzes */
.poll-bubble { min-width: 220px; }
.poll-question { font-weight: 600; font-size: 14px; margin: 4px 0 8px; }
.poll-options { display: flex; flex-direction: column; gap: 6px; }
.poll-option { position: relative; overflow: hidden; text-align: left; background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px; font-size: 13px; cursor: pointer; }
.poll-option:disabled { cursor: default; }
.poll-option-label { position: relative; z-index: 1; }
.poll-option-bar { position: absolute; left: 0; top: 0; bottom: 0; background: rgba(61,75,140,0.15); z-index: 0; }
.poll-option.mine .poll-option-bar { background: rgba(61,75,140,0.3); }
.poll-option.correct { border-color: #4CAF50; }
.poll-option.correct .poll-option-bar { background: rgba(76,175,80,0.25); }
.poll-option.incorrect { border-color: var(--danger); }
.poll-option-pct { position: absolute; right: 10px; top: 50%; transform: translateY(-50%); font-size: 12px; color: var(--ink-soft); z-index: 1; }
.poll-meta { font-size: 11px; color: var(--ink-soft); margin-top: 6px; }

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

.post-header-info { flex: 1; min-width: 0; }
.post-owner-actions { display: flex; gap: 4px; margin-left: auto; }
.post-owner-actions button, .comment-owner-actions button, .msg-owner-actions button { background: none; border: none; font-size: 13px; padding: 2px 4px; opacity: 0.6; }
.post-owner-actions button:hover, .comment-owner-actions button:hover, .msg-owner-actions button:hover { opacity: 1; }

.reaction-row { display: flex; gap: 4px; padding: 8px 0; flex-wrap: wrap; }
.reaction-row .reaction-btn { background: none; border: 1px solid var(--border); border-radius: 20px; padding: 4px 10px; font-size: 13px; color: var(--ink-soft); }
.reaction-row .reaction-btn.active { background: var(--paper); border-color: var(--indigo); color: var(--indigo-dark); font-weight: 600; }

.share-post-btn { background: none; border: 1px solid var(--border); border-radius: 7px; padding: 6px 12px; font-size: 13px; color: var(--ink-soft); }

.post-text a, .comment a, .chat-bubble a { color: var(--indigo); text-decoration: underline; word-break: break-all; }

.comment-body { display: flex; align-items: baseline; flex-wrap: wrap; gap: 4px; flex: 1; }
.comment-owner-actions { margin-left: auto; }

.msg-actions { display: flex; align-items: center; gap: 4px; margin-top: 4px; }
.reply-msg-btn { background: none; border: none; font-size: 11px; color: inherit; opacity: 0.6; padding: 0; }
.reply-msg-btn:hover { opacity: 1; }
.chat-bubble-row.mine .reply-msg-btn { color: #fff; }

.reply-quote { border-left: 3px solid var(--indigo); padding: 4px 8px; margin-bottom: 6px; font-size: 12px; background: rgba(61,75,140,0.08); border-radius: 4px; }
.chat-bubble-row.mine .reply-quote { background: rgba(255,255,255,0.15); border-left-color: #fff; }

.chat-bubble-row.pending { opacity: 0.6; }
.msg-status { font-size: 11px; margin-top: 3px; opacity: 0.8; }
.msg-status.failed { color: var(--danger); font-weight: 600; }
.chat-bubble-row.mine .msg-status:not(.failed) { color: rgba(255,255,255,0.8); }

#reply-banner:empty { display: none; }
.reply-banner-content { display: flex; align-items: center; justify-content: space-between; gap: 8px; padding: 8px 12px; background: var(--paper); border-top: 1px solid var(--border); font-size: 12px; color: var(--ink-soft); }
.reply-banner-content button { background: none; border: none; font-size: 14px; color: var(--ink-soft); }

.emoji-picker-popup { position: absolute; bottom: 100%; left: 0; margin-bottom: 4px; background: var(--card); border: 1px solid var(--border); border-radius: 10px; padding: 8px; box-shadow: 0 8px 20px -8px rgba(28,28,30,0.25); z-index: 60; display: flex; flex-wrap: wrap; gap: 4px; width: 190px; }
.emoji-option { font-size: 18px; cursor: pointer; padding: 3px; border-radius: 6px; }
.emoji-option:hover { background: var(--paper); }
.emoji-btn { background: none; border: 1px solid var(--border); border-radius: 7px; padding: 6px 10px; font-size: 14px; }

/* Notification bell */
.bell-btn { position: relative; background: none; border: none; font-size: 18px; padding: 4px; }
.bell-badge { position: absolute; top: -2px; right: -4px; background: var(--danger); color: #fff; font-size: 10px; font-weight: 700; border-radius: 10px; padding: 1px 5px; line-height: 1.3; }
.bell-dropdown { position: absolute; top: 100%; right: 0; margin-top: 8px; width: 280px; max-height: 360px; overflow-y: auto; background: var(--card); border: 1px solid var(--border); border-radius: 10px; box-shadow: 0 12px 28px -12px rgba(28,28,30,0.3); z-index: 200; }
.bell-item { padding: 10px 14px; border-bottom: 1px solid var(--border); font-size: 13px; cursor: pointer; }
.bell-item:hover { background: var(--paper); }
.bell-item strong { display: block; font-size: 13px; }
.bell-item div { color: var(--ink-soft); font-size: 12px; margin-top: 2px; }

/* Online status dot */
.avatar-wrap { position: relative; flex-shrink: 0; }
.online-dot { position: absolute; bottom: 0; right: 0; width: 10px; height: 10px; border-radius: 50%; background: #B8B8B8; border: 2px solid var(--card); }
.online-dot.online { background: #4CAF50; }

/* Typing indicator */
.typing-indicator { font-size: 12px; color: var(--ink-soft); padding: 0 16px; min-height: 18px; font-style: italic; }
.typing-indicator:empty { min-height: 0; }

/* Feed toggle + saved/report */
.feed-toggle { display: flex; gap: 6px; }
.feed-toggle-btn { flex: 1; background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 8px; font-size: 13px; font-weight: 600; color: var(--ink-soft); }
.feed-toggle-btn.active { background: var(--indigo); color: #fff; border-color: var(--indigo); }
.save-post-btn { background: none; border: 1px solid var(--border); border-radius: 7px; padding: 6px 12px; font-size: 13px; color: var(--ink-soft); }
.save-post-btn.active { color: var(--indigo); border-color: var(--indigo); font-weight: 600; }
.report-post-btn { background: none; border: 1px solid var(--border); border-radius: 7px; padding: 6px 12px; font-size: 12px; color: var(--ink-soft); }
.block-user-btn { background: none; border: none; font-size: 14px; padding: 2px 4px; }

/* Stories */
.stories-bar { display: flex; gap: 12px; overflow-x: auto; padding: 4px 2px 8px; }
.story-circle { flex-shrink: 0; display: flex; flex-direction: column; align-items: center; gap: 4px; cursor: pointer; width: 64px; position: relative; }
.story-circle .avatar-img, .story-circle .avatar { border: 2px solid var(--indigo); padding: 2px; }
.story-circle.add-story { position: relative; }
.story-plus { position: absolute; top: 40px; left: 40px; background: var(--indigo); color: #fff; width: 18px; height: 18px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 13px; font-weight: 700; border: 2px solid var(--card); }
.story-label { font-size: 11px; color: var(--ink-soft); text-align: center; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; max-width: 64px; }

.story-viewer-overlay { position: fixed; inset: 0; background: #000; z-index: 2500; display: flex; flex-direction: column; }
.story-viewer-header { display: flex; align-items: center; gap: 10px; padding: 12px; color: #fff; position: relative; z-index: 2; }
.story-progress { position: absolute; top: 6px; left: 12px; right: 12px; display: flex; gap: 4px; }
.story-progress span { flex: 1; height: 3px; background: rgba(255,255,255,0.3); border-radius: 2px; }
.story-progress span.filled { background: #fff; }
.story-viewer-author { display: flex; align-items: center; gap: 8px; margin-top: 10px; flex: 1; font-size: 13px; font-weight: 600; }
.story-viewer-header button { background: none; border: none; color: #fff; font-size: 18px; margin-top: 10px; }
.story-viewer-body { flex: 1; display: flex; align-items: center; justify-content: center; overflow: hidden; }
.story-viewer-body img, .story-viewer-body video { max-width: 100%; max-height: 100%; object-fit: contain; }
.story-viewer-nav { position: absolute; top: 0; bottom: 0; left: 0; right: 0; display: flex; }
.story-viewer-nav button { flex: 1; background: none; border: none; color: transparent; font-size: 0; }
.story-viewer-nav #story-prev-btn { cursor: w-resize; }
.story-viewer-nav #story-next-btn { cursor: e-resize; }

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
.chat-bubble .audio-embed { width: 260px; height: 54px; border: none; border-radius: 8px; max-width: 100%; }
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

.group-call-banner { display: flex; align-items: center; justify-content: space-between; gap: 10px; padding: 8px 16px; background: rgba(76,175,80,0.12); border-bottom: 1px solid var(--border); font-size: 13px; }
.group-call-banner button { background: #4CAF50; color: #fff; border: none; border-radius: 7px; padding: 6px 14px; font-size: 12px; font-weight: 600; }

.group-call-box { display: flex; flex-direction: column; align-items: center; gap: 16px; color: #fff; width: 100%; max-width: 480px; }
.group-call-header { font-family: 'Fraunces', serif; font-size: 18px; font-weight: 700; }
.group-call-grid { display: flex; flex-wrap: wrap; gap: 18px; justify-content: center; max-height: 60vh; overflow-y: auto; padding: 8px; }
.group-call-tile { display: flex; flex-direction: column; align-items: center; gap: 6px; width: 96px; }
.group-call-tile video { width: 96px; height: 96px; border-radius: 50%; object-fit: cover; border: 2px solid rgba(255,255,255,0.6); background: #222; }
.group-call-avatar { width: 96px; height: 96px; border-radius: 50%; display: flex; align-items: center; justify-content: center; border: 2px solid rgba(255,255,255,0.6); background: rgba(255,255,255,0.08); }
.group-call-avatar .avatar, .group-call-avatar .avatar-img { width: 64px !important; height: 64px !important; }
.group-call-name { font-size: 12px; color: rgba(255,255,255,0.85); text-align: center; max-width: 96px; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
.group-call-controls { display: flex; gap: 10px; }
.group-call-controls button { background: rgba(255,255,255,0.15); color: #fff; border: none; border-radius: 20px; padding: 10px 18px; font-size: 13px; font-weight: 600; }

.hidden { display: none !important; }

/* Splash screen */
#splash-screen {
  position: fixed; inset: 0; z-index: 9999;
  background: radial-gradient(circle at 30% 20%, #4A5CA8 0%, var(--indigo-dark) 55%, #1C2340 100%);
  display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 22px;
  transition: opacity 0.5s ease, visibility 0.5s ease;
}
#splash-screen.splash-hidden { opacity: 0; visibility: hidden; pointer-events: none; }

.splash-globe { width: 120px; height: 120px; perspective: 600px; }
.globe-sphere {
  width: 100%; height: 100%; border-radius: 50%; position: relative;
  background: radial-gradient(circle at 35% 30%, rgba(255,255,255,0.25), rgba(255,255,255,0.02) 60%), rgba(255,255,255,0.06);
  border: 1.5px solid rgba(255,255,255,0.5);
  box-shadow: 0 0 40px rgba(255,255,255,0.15), inset 0 0 30px rgba(255,255,255,0.1);
  animation: globe-spin 3.2s linear infinite;
  transform-style: preserve-3d;
}
.globe-line { position: absolute; border: 1px solid rgba(255,255,255,0.45); border-radius: 50%; }
.globe-lat { left: 0; right: 0; }
.globe-lat-1 { top: 20%; height: 60%; transform: scaleY(0.35); }
.globe-lat-2 { top: 0; height: 100%; transform: scaleY(1); }
.globe-lat-3 { top: 35%; height: 30%; transform: scaleY(0.2); }
.globe-lon { top: 0; bottom: 0; left: 50%; width: 100%; margin-left: -50%; }
.globe-lon-1 { transform: rotateY(0deg); border-radius: 50% / 50%; width: 60%; margin-left: -30%; }
.globe-lon-2 { transform: rotateY(90deg); }

@keyframes globe-spin {
  from { transform: rotateY(0deg) rotateX(8deg); }
  to { transform: rotateY(360deg) rotateX(8deg); }
}

.splash-brand { font-family: 'Fraunces', serif; font-weight: 700; font-size: 28px; color: #fff; letter-spacing: 0.5px; }
.splash-tagline { font-size: 14px; color: rgba(255,255,255,0.75); margin-top: -14px; }

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

/* Calls */
.call-btns { display: flex; gap: 6px; margin-left: auto; }
.call-btns button { background: none; border: 1px solid var(--border); border-radius: 7px; padding: 5px 9px; font-size: 15px; }

.call-overlay { position: fixed; inset: 0; background: rgba(20,20,22,0.92); display: flex; align-items: center; justify-content: center; z-index: 2000; padding: 16px; }
.call-box { display: flex; flex-direction: column; align-items: center; gap: 14px; color: #fff; text-align: center; }
.call-avatar { width: 84px; height: 84px; border-radius: 50%; background: var(--sage); color: #fff; display: flex; align-items: center; justify-content: center; font-size: 32px; font-weight: 700; }
.call-name { font-family: 'Fraunces', serif; font-size: 22px; font-weight: 700; }
.call-status { font-size: 14px; color: #C9C9CC; }
.call-actions { display: flex; gap: 14px; margin-top: 6px; }
.call-accept-btn { background: var(--sage); color: #fff; border: none; border-radius: 24px; padding: 12px 28px; font-size: 14px; font-weight: 600; }
.call-end-btn { background: var(--danger); color: #fff; border: none; border-radius: 24px; padding: 12px 28px; font-size: 14px; font-weight: 600; }

.call-box-video { position: relative; width: 100%; max-width: 600px; height: 80vh; max-height: 640px; }
.call-box-video audio { display: none; }
.remote-video { width: 100%; height: 100%; object-fit: cover; border-radius: 12px; background: #000; }
.local-video { position: absolute; bottom: 90px; right: 12px; width: 110px; height: 150px; object-fit: cover; border-radius: 8px; border: 2px solid #fff; background: #000; }
.call-controls { position: absolute; bottom: 16px; left: 0; right: 0; display: flex; justify-content: center; }
</style>
</head>
<body>

<div id="splash-screen">
  <div class="splash-globe">
    <div class="globe-sphere">
      <div class="globe-line globe-lat globe-lat-1"></div>
      <div class="globe-line globe-lat globe-lat-2"></div>
      <div class="globe-line globe-lat globe-lat-3"></div>
      <div class="globe-line globe-lon globe-lon-1"></div>
      <div class="globe-line globe-lon globe-lon-2"></div>
    </div>
  </div>
  <div class="splash-brand">Community</div>
  <div class="splash-tagline">Connect everyone, everywhere.</div>
</div>
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
let selectedFriend = null; // { userId, name, isGroup? } — set when a thread is open in the Inbox tab
let activeGroupInfo = null; // { groupId, name, createdBy, members } — populated when a group thread is open
let activeGroupCallBanner = null; // { groupCallId, callerName, type } — set if a call is already in progress for the open group
let showingSaved = false; // Feed tab: showing saved posts instead of the normal feed
let storyGroups = []; // active (non-expired) stories, grouped by author
let storyViewer = null; // { groupIndex, storyIndex } — active story being viewed, or null
let reelsList = [];
let reelsHasMore = true;
let onlineStatusMap = {}; // userId -> boolean, refreshed periodically for visible people
let incomingCallOverlayShown = null; // callId currently shown as an incoming-call popup
let notificationHistory = []; // rolling log of activity items, for the bell dropdown
let unreadNotificationCount = 0;
let bellDropdownOpen = false;

// Calls (WebRTC, signaled via polling the Apps Script sheet)
// STUN alone frequently fails to connect across different network types
// (mobile data <-> wifi, different ISPs, corporate NATs) — a TURN server
// relays media when a direct peer-to-peer path can't be established.
// Using the free Open Relay Project TURN service here.
const ICE_SERVERS = [
  { urls: 'stun:stun.l.google.com:19302' },
  { urls: 'stun:stun1.l.google.com:19302' },
  { urls: 'turn:openrelay.metered.ca:80', username: 'openrelayproject', credential: 'openrelayproject' },
  { urls: 'turn:openrelay.metered.ca:443', username: 'openrelayproject', credential: 'openrelayproject' },
  { urls: 'turn:openrelay.metered.ca:443?transport=tcp', username: 'openrelayproject', credential: 'openrelayproject' },
];
let activeCall = null; // { callId, role, type, pc, localStream, candidateSeen, statusInterval, startedAt }

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

function linkify(escapedText) {
  return escapedText.replace(/(https?:\/\/[^\s<]+)/g, (url) => `<a href="${url}" target="_blank" rel="noopener noreferrer">${url}</a>`);
}

const REACTIONS = [
  { type: 'like', emoji: '👍' },
  { type: 'love', emoji: '❤️' },
  { type: 'haha', emoji: '😂' },
  { type: 'wow', emoji: '😮' },
  { type: 'sad', emoji: '😢' },
];

const EMOJI_PALETTE = ['😀', '😂', '❤️', '👍', '🎉', '🔥', '😢', '😮', '🙏', '👏', '😅', '🤔'];

function attachEmojiPicker(btn, input) {
  btn.addEventListener('click', (e) => {
    e.stopPropagation();
    const existing = document.getElementById('emoji-picker-popup');
    if (existing) { existing.remove(); return; }
    const popup = document.createElement('div');
    popup.id = 'emoji-picker-popup';
    popup.className = 'emoji-picker-popup';
    popup.innerHTML = EMOJI_PALETTE.map(e => `<span class="emoji-option">${e}</span>`).join('');
    btn.parentElement.style.position = 'relative';
    btn.parentElement.appendChild(popup);
    popup.querySelectorAll('.emoji-option').forEach(opt => {
      opt.addEventListener('click', () => { input.value += opt.textContent; popup.remove(); input.focus(); });
    });
    setTimeout(() => {
      document.addEventListener('click', function handler(ev) {
        if (!popup.contains(ev.target) && ev.target !== btn) { popup.remove(); document.removeEventListener('click', handler); }
      });
    }, 0);
  });
}

function avatarHtml(name, photoURL, size) {
  size = size || 36;
  if (photoURL) {
    return `<img class="avatar-img" src="${photoURL}" style="width:${size}px;height:${size}px;" alt="" />`;
  }
  const initial = escapeHtml((name || '?')[0] || '?').toUpperCase();
  return `<div class="avatar" style="width:${size}px;height:${size}px;">${initial}</div>`;
}

let cachedFriends = null;
async function ensureFriendsCache() {
  if (!cachedFriends) {
    const res = await apiCall('getFriends', { userId: currentUser.userId });
    cachedFriends = res.friends;
  }
  return cachedFriends;
}

function extractMentions(text, friends) {
  const mentioned = [];
  friends.forEach(f => { if (text.indexOf('@' + f.name) !== -1) mentioned.push(f.userId); });
  return mentioned;
}

function attachMentionAutocomplete(inputEl) {
  let dropdown = null;
  function removeDropdown() { if (dropdown) { dropdown.remove(); dropdown = null; } }

  inputEl.addEventListener('input', async () => {
    const val = inputEl.value;
    const cursor = inputEl.selectionStart;
    const upToCursor = val.slice(0, cursor);
    const match = upToCursor.match(/@(\w*)$/);
    removeDropdown();
    if (!match) return;
    const query = match[1].toLowerCase();
    const friends = await ensureFriendsCache();
    const matches = friends.filter(f => f.name.toLowerCase().includes(query)).slice(0, 5);
    if (!matches.length) return;

    dropdown = document.createElement('div');
    dropdown.className = 'mention-dropdown';
    dropdown.innerHTML = matches.map(f => `<div class="mention-item" data-name="${escapeHtml(f.name)}">${escapeHtml(f.name)}</div>`).join('');
    inputEl.parentElement.style.position = 'relative';
    inputEl.parentElement.appendChild(dropdown);

    dropdown.querySelectorAll('.mention-item').forEach(item => {
      item.addEventListener('mousedown', (e) => {
        e.preventDefault();
        const name = item.dataset.name;
        const newVal = val.slice(0, cursor - match[0].length) + '@' + name + ' ' + val.slice(cursor);
        inputEl.value = newVal;
        removeDropdown();
        inputEl.focus();
      });
    });
  });
  inputEl.addEventListener('blur', () => setTimeout(removeDropdown, 150));
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
  startBackgroundSync();

  stopFeedPolling();
  stopConversationPolling();

  if (currentTab === 'feed') { renderFeedPanel(); startFeedPolling(); }
  else if (currentTab === 'reels') { renderReelsPanel(); }
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
          <button id="tab-reels" class="${currentTab === 'reels' ? 'active' : ''}">Reels</button>
          <button id="tab-chat" class="${currentTab === 'chat' ? 'active' : ''}">Chat</button>
          <button id="tab-people" class="${currentTab === 'people' ? 'active' : ''}">People</button>
          <button id="tab-inbox" class="${currentTab === 'inbox' ? 'active' : ''}">Inbox</button>
        </div>
      </div>
      <div class="nav-user">
        <button id="bell-btn" class="bell-btn" title="Notifications">🔔${unreadNotificationCount > 0 ? `<span class="bell-badge">${unreadNotificationCount > 9 ? '9+' : unreadNotificationCount}</span>` : ''}</button>
        <span id="profile-open-btn" class="profile-name-btn">
          ${avatarHtml(currentUser.name, currentUser.photoURL, 26)}
          ${escapeHtml(currentUser.name)}
        </span>
        <button id="logout-btn">Log out</button>
      </div>
    </nav>
    <main class="main ${currentTab === 'chat' || currentTab === 'inbox' ? 'main-chat' : ''} ${currentTab === 'reels' ? 'main-reels' : ''}" id="main-panel"></main>
  </div>`;
}

function attachShellHandlers() {
  document.getElementById('tab-feed').addEventListener('click', () => { currentTab = 'feed'; render(); });
  document.getElementById('tab-reels').addEventListener('click', () => { currentTab = 'reels'; render(); });
  document.getElementById('tab-chat').addEventListener('click', () => { currentTab = 'chat'; render(); });
  document.getElementById('tab-people').addEventListener('click', () => { currentTab = 'people'; render(); });
  document.getElementById('tab-inbox').addEventListener('click', () => { currentTab = 'inbox'; render(); });
  document.getElementById('profile-open-btn').addEventListener('click', openProfileModal);
  document.getElementById('bell-btn').addEventListener('click', toggleBellDropdown);
  document.getElementById('logout-btn').addEventListener('click', () => {
    localStorage.removeItem(USER_KEY);
    currentUser = null;
    stopFeedPolling(); stopConversationPolling(); stopBackgroundSync();
    if (activeCall) hangupCall();
    if (groupCallState) leaveGroupCallFlow();
    stopRingtone(); stopRingback();
    cachedFriends = null;
    notificationHistory = []; unreadNotificationCount = 0;
    render();
  });
}

/* ============================================================
   Feed
   ============================================================ */
let latestPostTimestamp = null;

async function loadFirstPage() {
  const res = await apiCall('getPosts', { offset: 0, limit: 10, userId: currentUser.userId });
  feedPosts = res.posts;
  feedHasMore = res.hasMore;
  latestPostTimestamp = feedPosts.length ? feedPosts[0].createdAt : new Date().toISOString();
  renderFeedPanel();
  loadStories();
}

async function loadMorePosts() {
  const res = await apiCall('getPosts', { offset: feedPosts.length, limit: 10, userId: currentUser.userId });
  feedPosts = feedPosts.concat(res.posts);
  feedHasMore = res.hasMore;
  renderFeedPanel();
}

async function pollFeedForNewPosts() {
  if (!latestPostTimestamp || showingSaved) return;
  try {
    const res = await apiCall('getPosts', { since: latestPostTimestamp, userId: currentUser.userId });
    if (res.posts.length) {
      feedPosts = res.posts.concat(feedPosts);
      latestPostTimestamp = res.posts[0].createdAt;
      renderFeedPanel();
    }
  } catch (err) { /* silent — background poll */ }
}

function startFeedPolling() {
  if (feedInterval) return;
  loadFirstPage();
  feedInterval = setInterval(pollFeedForNewPosts, 15000);
}
function stopFeedPolling() { if (feedInterval) { clearInterval(feedInterval); feedInterval = null; } }

function reactionsRowHtml(post) {
  const counts = post.reactionCounts || {};
  const mine = post.myReaction;
  return `<div class="reaction-row" data-post-id="${post.postId}">` +
    REACTIONS.map(r => `<button class="reaction-btn ${mine === r.type ? 'active' : ''}" data-type="${r.type}">${r.emoji}${counts[r.type] ? ' ' + counts[r.type] : ''}</button>`).join('') +
    `</div>`;
}

function postCardHtml(post) {
  const comments = commentsCache[post.postId] || [];
  const showComments = !!openComments[post.postId];
  const isMine = post.authorId === currentUser.userId;
  return `
  <article class="post-card" data-post-id="${post.postId}">
    <header class="post-header">
      ${avatarHtml(post.authorName, post.authorPhoto)}
      <div class="post-header-info">
        <div class="post-author">${escapeHtml(post.authorName)}</div>
        <div class="post-time">${post.createdAt ? new Date(post.createdAt).toLocaleString() : 'just now'}</div>
      </div>
      ${isMine ? `
        <div class="post-owner-actions">
          <button class="edit-post-btn" data-post-id="${post.postId}" title="Edit">✏️</button>
          <button class="delete-post-btn" data-post-id="${post.postId}" title="Delete">🗑️</button>
        </div>` : ''}
    </header>
    ${post.text ? `<p class="post-text">${linkify(escapeHtml(post.text))}</p>` : ''}
    ${post.imageURL ? `<img class="post-image" src="${post.imageURL}" alt="" />` : ''}
    ${reactionsRowHtml(post)}
    <div class="post-actions">
      <button class="comment-toggle-btn" data-post-id="${post.postId}">💬 ${post.commentCount ?? comments.length}</button>
      <button class="share-post-btn" data-post-id="${post.postId}">↗ Share</button>
      <button class="save-post-btn ${post.saved ? 'active' : ''}" data-post-id="${post.postId}">${post.saved ? '🔖 Saved' : '🔖 Save'}</button>
      ${!isMine ? `<button class="report-post-btn" data-post-id="${post.postId}">⚑ Report</button>` : ''}
    </div>
    <div class="comments ${showComments ? '' : 'hidden'}" data-comments-for="${post.postId}">
      ${comments.map(commentHtml).join('')}
      <form class="comment-form" data-post-id="${post.postId}">
        <input placeholder="Write a comment…" />
        <button type="button" class="emoji-btn">😊</button>
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
      <div class="stories-bar" id="stories-bar">${storiesBarHtml()}</div>
      <div class="feed-toggle">
        <button class="feed-toggle-btn ${!showingSaved ? 'active' : ''}" id="show-all-btn">All</button>
        <button class="feed-toggle-btn ${showingSaved ? 'active' : ''}" id="show-saved-btn">🔖 Saved</button>
      </div>
      ${showingSaved ? '' : `
      <div class="create-post">
        <textarea id="new-post-text" placeholder="Share something with the community…" rows="3"></textarea>
        <div class="create-post-row">
          <label class="file-btn">
            <span id="new-post-filename">Add photo</span>
            <input type="file" id="new-post-image" accept="image/*" hidden />
          </label>
          <button type="button" id="new-post-submit">Post</button>
        </div>
      </div>`}
      ${feedPosts.length === 0 ? `<p class="empty-state">${showingSaved ? 'No saved posts yet.' : 'Nothing here yet — be the first to post.'}</p>` : ''}
      ${feedPosts.map(postCardHtml).join('')}
      ${!showingSaved && feedHasMore ? '<button class="load-more" id="load-more-btn">Load more</button>' : ''}
    </div>`;
  attachFeedHandlers();
}

/* ============================================================
   Reels — vertical video feed
   ============================================================ */
async function renderReelsPanel() {
  const panel = document.getElementById('main-panel');
  panel.innerHTML = `<div class="reels-container" id="reels-container"><p class="empty-state" style="color:#fff;">Loading…</p></div>`;
  const res = await apiCall('getReels', { offset: 0, limit: 10, userId: currentUser.userId });
  reelsList = res.reels;
  reelsHasMore = res.hasMore;
  renderReelsList();
}

function renderReelsList() {
  const container = document.getElementById('reels-container');
  if (!container) return;
  container.innerHTML = `
    <button id="upload-reel-btn" class="upload-reel-btn">+ Reel</button>
    ${reelsList.length === 0 ? '<p class="empty-state" style="color:#fff;">No reels yet — be the first to upload.</p>' : ''}
    ${reelsList.map(reelCardHtml).join('')}
    ${reelsHasMore ? '<button class="load-more-reel-btn" id="load-more-reels-btn">Load more</button>' : ''}
  `;
  document.getElementById('upload-reel-btn').addEventListener('click', uploadReel);
  const moreBtn = document.getElementById('load-more-reels-btn');
  if (moreBtn) moreBtn.addEventListener('click', loadMoreReels);

  document.querySelectorAll('.reel-like-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      const reelId = btn.dataset.reelId;
      try {
        const res = await apiCall('likeReel', { reelId, userId: currentUser.userId });
        const reel = reelsList.find(r => r.reelId === reelId);
        if (reel) { reel.liked = res.liked; reel.likeCount = res.likeCount; }
        btn.classList.toggle('active', res.liked);
        btn.querySelector('.reel-like-count').textContent = res.likeCount;
      } catch (err) { console.error(err); }
    });
  });
}

function reelCardHtml(reel) {
  return `
  <div class="reel-card">
    <video src="${reel.videoURL}" loop playsinline controls class="reel-video"></video>
    <div class="reel-overlay">
      <div class="reel-author">${avatarHtml(reel.authorName, reel.authorPhoto, 32)}<span>${escapeHtml(reel.authorName)}</span></div>
      ${reel.caption ? `<div class="reel-caption">${linkify(escapeHtml(reel.caption))}</div>` : ''}
      <button class="reel-like-btn ${reel.liked ? 'active' : ''}" data-reel-id="${reel.reelId}">❤️ <span class="reel-like-count">${reel.likeCount || 0}</span></button>
    </div>
  </div>`;
}

async function loadMoreReels() {
  const res = await apiCall('getReels', { offset: reelsList.length, limit: 10, userId: currentUser.userId });
  reelsList = reelsList.concat(res.reels);
  reelsHasMore = res.hasMore;
  renderReelsList();
}

function uploadReel() {
  const input = document.createElement('input');
  input.type = 'file';
  input.accept = 'video/*';
  input.onchange = async () => {
    const file = input.files[0];
    if (!file) return;
    const caption = prompt('Add a caption (optional):') || '';
    try {
      const base64 = await fileToBase64(file);
      const res = await apiCall('createReel', { authorId: currentUser.userId, authorName: currentUser.name, authorPhoto: currentUser.photoURL || '', videoBase64: base64, videoMime: file.type, videoName: file.name, caption });
      reelsList = [res.reel].concat(reelsList);
      renderReelsList();
    } catch (err) { alert('Failed to upload reel: ' + err.message); }
  };
  input.click();
}

/* ============================================================
   Stories — 24hr photo/video, shown as a bar of circles above the feed
   ============================================================ */
function storiesBarHtml() {
  const mine = storyGroups.find(g => g.authorId === currentUser.userId);
  const others = storyGroups.filter(g => g.authorId !== currentUser.userId);
  const selfCircle = `
    <div class="story-circle add-story" id="add-story-btn">
      ${avatarHtml(currentUser.name, currentUser.photoURL, 56)}
      <span class="story-plus">+</span>
      <div class="story-label">${mine ? 'Your story' : 'Add story'}</div>
    </div>`;
  const otherCircles = others.map((g, i) => `
    <div class="story-circle" data-group-id="${g.authorId}">
      ${avatarHtml(g.authorName, g.authorPhoto, 56)}
      <div class="story-label">${escapeHtml(g.authorName.split(' ')[0])}</div>
    </div>`).join('');
  return selfCircle + (mine ? `
    <div class="story-circle" data-group-id="${mine.authorId}">
      ${avatarHtml(mine.authorName, mine.authorPhoto, 56)}
      <div class="story-label">View</div>
    </div>` : '') + otherCircles;
}

async function loadStories() {
  try {
    const res = await apiCall('getActiveStories', { userId: currentUser.userId });
    storyGroups = res.groups;
    const bar = document.getElementById('stories-bar');
    if (bar) { bar.innerHTML = storiesBarHtml(); attachStoriesBarHandlers(); }
  } catch (err) { /* silent */ }
}

function attachStoriesBarHandlers() {
  const addBtn = document.getElementById('add-story-btn');
  if (addBtn) addBtn.addEventListener('click', uploadStory);
  document.querySelectorAll('.story-circle[data-group-id]').forEach(el => {
    el.addEventListener('click', () => openStoryViewer(el.dataset.groupId));
  });
}

async function uploadStory() {
  const input = document.createElement('input');
  input.type = 'file';
  input.accept = 'image/*,video/*';
  input.onchange = async () => {
    const file = input.files[0];
    if (!file) return;
    try {
      const base64 = await fileToBase64(file);
      await apiCall('createStory', { authorId: currentUser.userId, authorName: currentUser.name, authorPhoto: currentUser.photoURL || '', mediaBase64: base64, mediaMime: file.type, mediaName: file.name });
      loadStories();
    } catch (err) { alert('Failed to post story: ' + err.message); }
  };
  input.click();
}

function openStoryViewer(authorId) {
  const groupIndex = storyGroups.findIndex(g => g.authorId === authorId);
  if (groupIndex === -1) return;
  storyViewer = { groupIndex, storyIndex: 0 };
  renderStoryViewer();
}

function renderStoryViewer() {
  if (!storyViewer) { const el = document.getElementById('story-viewer-overlay'); if (el) el.remove(); return; }
  const group = storyGroups[storyViewer.groupIndex];
  const story = group.stories[storyViewer.storyIndex];

  let overlay = document.getElementById('story-viewer-overlay');
  if (!overlay) {
    overlay = document.createElement('div');
    overlay.id = 'story-viewer-overlay';
    overlay.className = 'story-viewer-overlay';
    document.body.appendChild(overlay);
  }
  overlay.innerHTML = `
    <div class="story-viewer-header">
      <div class="story-progress">${group.stories.map((s, i) => `<span class="${i <= storyViewer.storyIndex ? 'filled' : ''}"></span>`).join('')}</div>
      <div class="story-viewer-author">${avatarHtml(group.authorName, group.authorPhoto, 28)}<span>${escapeHtml(group.authorName)}</span></div>
      <button id="story-close-btn">✕</button>
    </div>
    <div class="story-viewer-body">
      ${story.type === 'video' ? `<video src="${story.mediaURL}" autoplay controls></video>` : `<img src="${story.mediaURL}" alt="" />`}
    </div>
    <div class="story-viewer-nav">
      <button id="story-prev-btn">‹</button>
      <button id="story-next-btn">›</button>
    </div>`;

  document.getElementById('story-close-btn').addEventListener('click', () => { storyViewer = null; renderStoryViewer(); });
  document.getElementById('story-prev-btn').addEventListener('click', () => stepStory(-1));
  document.getElementById('story-next-btn').addEventListener('click', () => stepStory(1));
}

function stepStory(delta) {
  const group = storyGroups[storyViewer.groupIndex];
  let newStoryIndex = storyViewer.storyIndex + delta;
  if (newStoryIndex >= group.stories.length) {
    if (storyViewer.groupIndex + 1 < storyGroups.length) { storyViewer = { groupIndex: storyViewer.groupIndex + 1, storyIndex: 0 }; renderStoryViewer(); }
    else { storyViewer = null; renderStoryViewer(); }
    return;
  }
  if (newStoryIndex < 0) {
    if (storyViewer.groupIndex - 1 >= 0) { const prevGroup = storyGroups[storyViewer.groupIndex - 1]; storyViewer = { groupIndex: storyViewer.groupIndex - 1, storyIndex: prevGroup.stories.length - 1 }; renderStoryViewer(); }
    return;
  }
  storyViewer.storyIndex = newStoryIndex;
  renderStoryViewer();
}

async function showSavedPosts() {
  showingSaved = true;
  const res = await apiCall('getSavedPosts', { userId: currentUser.userId });
  feedPosts = res.posts;
  renderFeedPanel();
}

async function showAllPosts() {
  showingSaved = false;
  await loadFirstPage();
}

function attachFeedHandlers() {
  attachStoriesBarHandlers();
  document.getElementById('show-all-btn').addEventListener('click', showAllPosts);
  document.getElementById('show-saved-btn').addEventListener('click', showSavedPosts);

  const imageInput = document.getElementById('new-post-image');
  if (imageInput) {
    imageInput.addEventListener('change', () => {
      document.getElementById('new-post-filename').textContent = imageInput.files[0] ? imageInput.files[0].name : 'Add photo';
    });
    attachMentionAutocomplete(document.getElementById('new-post-text'));

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
        const friends = await ensureFriendsCache();
        const mentions = extractMentions(text, friends);
        const res = await apiCall('createPost', {
          authorId: currentUser.userId, authorName: currentUser.name, authorPhoto: currentUser.photoURL || '',
          text, imageBase64, imageMime: file?.type, imageName: file?.name, mentions,
        });
        textEl.value = ''; imageInput.value = '';
        feedPosts = [res.post].concat(feedPosts);
        latestPostTimestamp = res.post.createdAt;
        renderFeedPanel();
      } catch (err) {
        alert('Failed to post: ' + err.message);
      } finally {
        btn.disabled = false; btn.textContent = 'Post';
      }
    });
  }

  const loadMoreBtn = document.getElementById('load-more-btn');
  if (loadMoreBtn) loadMoreBtn.addEventListener('click', async () => {
    loadMoreBtn.disabled = true; loadMoreBtn.textContent = 'Loading…';
    await loadMorePosts();
  });

  document.querySelectorAll('.reaction-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      const row = btn.closest('.reaction-row');
      const postId = row.dataset.postId;
      const type = btn.dataset.type;
      try {
        const res = await apiCall('setReaction', { postId, userId: currentUser.userId, type });
        const post = feedPosts.find(p => p.postId === postId);
        if (post) { post.reactionCounts = res.counts; post.myReaction = res.myReaction; }
        renderFeedPanel();
      } catch (err) { console.error(err); }
    });
  });

  document.querySelectorAll('.edit-post-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      const postId = btn.dataset.postId;
      const post = feedPosts.find(p => p.postId === postId);
      const newText = prompt('Edit post:', post.text || '');
      if (newText === null || newText.trim() === '') return;
      try {
        await apiCall('updatePost', { postId, userId: currentUser.userId, text: newText.trim() });
        post.text = newText.trim();
        renderFeedPanel();
      } catch (err) { alert(err.message); }
    });
  });

  document.querySelectorAll('.delete-post-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      if (!confirm('Delete this post?')) return;
      const postId = btn.dataset.postId;
      try {
        await apiCall('deletePost', { postId, userId: currentUser.userId });
        feedPosts = feedPosts.filter(p => p.postId !== postId);
        renderFeedPanel();
      } catch (err) { alert(err.message); }
    });
  });

  document.querySelectorAll('.share-post-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      const postId = btn.dataset.postId;
      const post = feedPosts.find(p => p.postId === postId);
      const shareText = `${post.authorName} on Community: ${post.text || '(photo)'}`;
      try {
        if (navigator.share) {
          await navigator.share({ text: shareText });
        } else {
          await navigator.clipboard.writeText(shareText);
          alert('Post copied — paste it anywhere to share.');
        }
      } catch (err) { /* user cancelled share sheet — ignore */ }
    });
  });

  document.querySelectorAll('.save-post-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      const postId = btn.dataset.postId;
      try {
        const res = await apiCall('savePost', { userId: currentUser.userId, postId });
        if (showingSaved && !res.saved) {
          feedPosts = feedPosts.filter(p => p.postId !== postId);
        } else {
          const post = feedPosts.find(p => p.postId === postId);
          if (post) post.saved = res.saved;
        }
        renderFeedPanel();
      } catch (err) { alert(err.message); }
    });
  });

  document.querySelectorAll('.report-post-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      const reason = prompt('Why are you reporting this post? (optional)') || '';
      try {
        await apiCall('reportContent', { reporterId: currentUser.userId, targetType: 'post', targetId: btn.dataset.postId, reason });
        alert('Thanks — this post has been reported.');
      } catch (err) { alert(err.message); }
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
    const input = form.querySelector('input');
    attachMentionAutocomplete(input);
    attachEmojiPicker(form.querySelector('.emoji-btn'), input);
    form.addEventListener('submit', async (e) => {
      e.preventDefault();
      const postId = form.dataset.postId;
      const text = input.value.trim();
      if (!text) return;
      input.value = '';
      const friends = await ensureFriendsCache();
      const mentions = extractMentions(text, friends);
      const res = await apiCall('addComment', { postId, authorId: currentUser.userId, authorName: currentUser.name, authorPhoto: currentUser.photoURL || '', text, mentions });
      commentsCache[postId] = (commentsCache[postId] || []).concat([res.comment]);
      renderCommentsInto(form.parentElement, postId);
    });
  });

  document.querySelectorAll('[data-comments-for]').forEach(container => {
    attachCommentOwnerHandlers(container, container.dataset.commentsFor);
  });
}

function commentHtml(c) {
  const isMine = c.authorId === currentUser.userId;
  return `<div class="comment" data-comment-id="${c.commentId}">
    ${avatarHtml(c.authorName, c.authorPhoto, 24)}
    <div class="comment-body">
      <span class="comment-author">${escapeHtml(c.authorName)}</span> ${linkify(escapeHtml(c.text))}
      ${isMine ? `<span class="comment-owner-actions"><button class="edit-comment-btn" data-comment-id="${c.commentId}" data-post-id="${c.postId}">✏️</button><button class="delete-comment-btn" data-comment-id="${c.commentId}" data-post-id="${c.postId}">🗑️</button></span>` : ''}
    </div>
  </div>`;
}

function renderCommentsInto(container, postId) {
  const comments = commentsCache[postId] || [];
  const formHtml = `<form class="comment-form" data-post-id="${postId}"><input placeholder="Write a comment…" /><button type="button" class="emoji-btn">😊</button><button type="submit">Send</button></form>`;
  container.innerHTML = comments.map(commentHtml).join('') + formHtml;
  const input = container.querySelector('.comment-form input');
  attachMentionAutocomplete(input);
  attachEmojiPicker(container.querySelector('.emoji-btn'), input);
  attachCommentOwnerHandlers(container, postId);
  container.querySelector('.comment-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const text = input.value.trim();
    if (!text) return;
    input.value = '';
    const friends = await ensureFriendsCache();
    const mentions = extractMentions(text, friends);
    const res = await apiCall('addComment', { postId, authorId: currentUser.userId, authorName: currentUser.name, authorPhoto: currentUser.photoURL || '', text, mentions });
    commentsCache[postId] = (commentsCache[postId] || []).concat([res.comment]);
    renderCommentsInto(container, postId);
  });
}

function attachCommentOwnerHandlers(container, postId) {
  container.querySelectorAll('.edit-comment-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      const commentId = btn.dataset.commentId;
      const comment = (commentsCache[postId] || []).find(c => c.commentId === commentId);
      const newText = prompt('Edit comment:', comment?.text || '');
      if (newText === null || newText.trim() === '') return;
      try {
        await apiCall('updateComment', { commentId, userId: currentUser.userId, text: newText.trim() });
        comment.text = newText.trim();
        renderCommentsInto(container, postId);
      } catch (err) { alert(err.message); }
    });
  });
  container.querySelectorAll('.delete-comment-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      if (!confirm('Delete this comment?')) return;
      const commentId = btn.dataset.commentId;
      try {
        await apiCall('deleteComment', { commentId, userId: currentUser.userId });
        commentsCache[postId] = (commentsCache[postId] || []).filter(c => c.commentId !== commentId);
        const post = feedPosts.find(p => p.postId === postId);
        if (post) post.commentCount = Math.max(0, (post.commentCount || 1) - 1);
        renderCommentsInto(container, postId);
      } catch (err) { alert(err.message); }
    });
  });
}

/* ============================================================
   Chat (generalized — powers both the community room and DMs)
   ============================================================ */
let currentTypingUsers = [];

async function loadConversationInitial() {
  const res = await apiCall('getMessages', { conversationId: activeConversationId, userId: currentUser.userId });
  conversationMessages = res.messages;
  conversationLastTimestamp = conversationMessages.length
    ? conversationMessages[conversationMessages.length - 1].createdAt
    : null;
  currentTypingUsers = res.typingUsers || [];
  renderChatPanel();
}

async function pollConversation() {
  const res = await apiCall('getMessages', { conversationId: activeConversationId, since: conversationLastTimestamp, userId: currentUser.userId });
  const typingChanged = JSON.stringify(res.typingUsers || []) !== JSON.stringify(currentTypingUsers);
  currentTypingUsers = res.typingUsers || [];
  if (res.messages.length) {
    conversationMessages = conversationMessages.concat(res.messages);
    conversationLastTimestamp = res.messages[res.messages.length - 1].createdAt;
    renderChatPanel();
  } else if (typingChanged) {
    updateTypingIndicator();
  }
}

function updateTypingIndicator() {
  const el = document.getElementById('typing-indicator');
  if (!el) return;
  if (!currentTypingUsers.length) { el.textContent = ''; return; }
  el.textContent = conversationKind(activeConversationId) === 'dm'
    ? `${activeConversationTitle} is typing…`
    : 'Someone is typing…';
}

function enterConversation(conversationId, title) {
  activeConversationId = conversationId;
  activeConversationTitle = title || null;
  conversationMessages = [];
  conversationLastTimestamp = null;
  replyingTo = null;
  stopConversationPolling();
  loadConversationInitial();
  conversationInterval = setInterval(pollConversation, 2500);
}

function stopConversationPolling() { if (conversationInterval) { clearInterval(conversationInterval); conversationInterval = null; } }

function exitToInboxList() {
  stopConversationPolling();
  selectedFriend = null;
  activeGroupInfo = null;
  activeGroupCallBanner = null;
  renderInboxPanel();
}

let replyingTo = null; // { messageId, text, senderName } — snapshot shown as a banner above the input

function pollBubbleHtml(m) {
  const options = m.pollOptions || [];
  const counts = m.pollCounts || {};
  const total = m.pollTotalVotes || 0;
  const myVote = m.pollMyVote;
  const showResults = myVote !== null && myVote !== undefined;

  const optionsHtml = options.map((opt, i) => {
    const voteCount = counts[i] || 0;
    const pct = total ? Math.round((voteCount / total) * 100) : 0;
    const isMine = myVote === i;
    const isCorrect = m.pollIsQuiz && i === m.pollCorrectIndex;
    const resultClass = showResults && m.pollIsQuiz ? (isCorrect ? 'correct' : (isMine ? 'incorrect' : '')) : '';
    return `
      <button class="poll-option ${isMine ? 'mine' : ''} ${resultClass}" data-message-id="${m.messageId}" data-option-index="${i}" ${showResults ? 'disabled' : ''}>
        <span class="poll-option-label">${escapeHtml(opt)} ${showResults && m.pollIsQuiz && isCorrect ? '✓' : ''}</span>
        ${showResults ? `<span class="poll-option-bar" style="width:${pct}%"></span><span class="poll-option-pct">${pct}%</span>` : ''}
      </button>`;
  }).join('');

  return `
  <div class="chat-bubble-row" data-message-id="${m.messageId}">
    <div class="chat-bubble poll-bubble">
      <div class="chat-sender">${escapeHtml(m.senderName)} ${m.pollIsQuiz ? 'started a quiz' : 'started a poll'}</div>
      <p class="poll-question">${escapeHtml(m.text)}</p>
      <div class="poll-options">${optionsHtml}</div>
      <div class="poll-meta">${total} vote${total === 1 ? '' : 's'}</div>
    </div>
  </div>`;
}

function chatBubbleHtml(m) {
  if (m.type === 'poll') return pollBubbleHtml(m);
  const mine = m.senderId === currentUser.userId;
  let mediaHtml = '';
  if (m.type === 'audio') mediaHtml = `<iframe src="${m.mediaURL}" class="audio-embed" allow="autoplay"></iframe>`;
  else if (m.type === 'video') mediaHtml = `<video controls src="${m.mediaURL}"></video>`;
  else if (m.type === 'image') mediaHtml = `<img src="${m.mediaURL}" alt="" />`;

  let replyPreview = '';
  let replyObj = null;
  try { replyObj = m.replyTo && m.replyTo !== 'null' ? (typeof m.replyTo === 'string' ? JSON.parse(m.replyTo) : m.replyTo) : null; } catch (e) { replyObj = null; }
  if (replyObj) replyPreview = `<div class="reply-quote"><strong>${escapeHtml(replyObj.senderName)}</strong> ${escapeHtml((replyObj.text || '').slice(0, 60))}</div>`;

  const ownerActions = mine && !m._pending ? `
    <span class="msg-owner-actions">
      ${m.type === 'text' ? `<button class="edit-msg-btn" data-message-id="${m.messageId}">✏️</button>` : ''}
      <button class="delete-msg-btn" data-message-id="${m.messageId}">🗑️</button>
    </span>` : '';

  const statusHtml = m._pending ? `<div class="msg-status">Sending…</div>` : m._failed ? `<div class="msg-status failed">Failed to send</div>` : '';

  return `
  <div class="chat-bubble-row ${mine ? 'mine' : ''} ${m._pending ? 'pending' : ''}" data-message-id="${m.messageId}">
    ${!mine ? avatarHtml(m.senderName, m.senderPhoto, 28) : ''}
    <div class="chat-bubble">
      ${!mine ? `<div class="chat-sender">${escapeHtml(m.senderName)}</div>` : ''}
      ${replyPreview}
      ${m.type === 'text' ? `<p>${linkify(escapeHtml(m.text))}</p>` : mediaHtml}
      ${statusHtml}
      ${!m._pending ? `<div class="msg-actions">
        <button class="reply-msg-btn" data-message-id="${m.messageId}" data-sender-name="${escapeHtml(m.senderName)}" data-text="${escapeHtml((m.text || (m.type + ' message')).slice(0, 60))}">↩ Reply</button>
        ${ownerActions}
      </div>` : ''}
    </div>
  </div>`;
}

function conversationKind(conversationId) {
  if (conversationId === 'general') return 'community';
  if (conversationId.startsWith('dm_')) return 'dm';
  if (conversationId.startsWith('group_')) return 'group';
  return 'unknown';
}

function renderChatPanel() {
  const panel = document.getElementById('main-panel');
  if (!panel) return;
  const isDm = !!activeConversationTitle;
  const kind = conversationKind(activeConversationId);
  const isDirectDm = kind === 'dm';
  const isGroupConvo = kind === 'group';
  const canManageGroup = isGroupConvo && activeGroupInfo && activeGroupInfo.createdBy === currentUser.userId;
  const headerHtml = isDm ? `
    <div class="chat-thread-header">
      <button id="chat-back-btn">← Back</button>
      <span>${escapeHtml(activeConversationTitle)}</span>
      ${isDirectDm || isGroupConvo ? `
        <div class="call-btns">
          <button id="audio-call-btn" title="Audio call">📞</button>
          <button id="video-call-btn" title="Video call">🎥</button>
        </div>` : ''}
      ${canManageGroup ? `<button id="manage-group-btn" class="small-action-btn">Manage</button>` : ''}
    </div>
    ${isGroupConvo && activeGroupCallBanner ? `
      <div class="group-call-banner">
        <span>📞 ${escapeHtml(activeGroupCallBanner.callerName)} started a ${activeGroupCallBanner.type} call</span>
        <button id="join-group-call-banner-btn">Join</button>
      </div>` : ''}` : '';
  const placeholder = isDm ? `Message ${escapeHtml(activeConversationTitle)}…` : 'Message the community…';

  panel.innerHTML = `
    <div class="chat">
      ${headerHtml}
      <div class="chat-messages" id="chat-messages">
        ${conversationMessages.map(chatBubbleHtml).join('')}
      </div>
      <div id="typing-indicator" class="typing-indicator">${currentTypingUsers.length ? (conversationKind(activeConversationId) === 'dm' ? escapeHtml(activeConversationTitle) + ' is typing…' : 'Someone is typing…') : ''}</div>
      <div id="recording-area"></div>
      <div id="reply-banner"></div>
      <form class="chat-input-row" id="chat-form">
        <button type="button" id="attach-btn" title="Send photo/video">📎</button>
        <input type="file" id="attach-input" accept="image/*,video/*" hidden />
        <button type="button" id="rec-audio-btn" title="Record audio">🎤</button>
        <button type="button" id="rec-video-btn" title="Record video">🎥</button>
        <button type="button" id="poll-btn" title="Create poll/quiz">📊</button>
        <button type="button" class="emoji-btn" title="Emoji">😊</button>
        <input id="chat-text" placeholder="${placeholder}" />
        <button type="submit">Send</button>
      </form>
    </div>`;
  const msgBox = document.getElementById('chat-messages');
  msgBox.scrollTop = msgBox.scrollHeight;
  if (isDm) document.getElementById('chat-back-btn').addEventListener('click', exitToInboxList);
  if (isDirectDm) {
    document.getElementById('audio-call-btn').addEventListener('click', () => initiateCall(selectedFriend.userId, selectedFriend.name, 'audio'));
    document.getElementById('video-call-btn').addEventListener('click', () => initiateCall(selectedFriend.userId, selectedFriend.name, 'video'));
  }
  if (isGroupConvo) {
    document.getElementById('audio-call-btn').addEventListener('click', () => startGroupVideoCall(activeGroupInfo?.groupId || selectedFriend.userId, activeConversationTitle, 'audio'));
    document.getElementById('video-call-btn').addEventListener('click', () => startGroupVideoCall(activeGroupInfo?.groupId || selectedFriend.userId, activeConversationTitle, 'video'));
    const joinBtn = document.getElementById('join-group-call-banner-btn');
    if (joinBtn) joinBtn.addEventListener('click', () => joinGroupCallFlow(activeGroupCallBanner.groupCallId, activeGroupInfo?.groupId || selectedFriend.userId, activeConversationTitle, activeGroupCallBanner.type));
  }
  if (canManageGroup) {
    document.getElementById('manage-group-btn').addEventListener('click', openManageGroupModal);
  }
  attachChatHandlers();
}

async function openCreatePollModal() {
  const existing = document.getElementById('poll-modal-overlay');
  if (existing) existing.remove();

  const overlay = document.createElement('div');
  overlay.id = 'poll-modal-overlay';
  overlay.className = 'modal-overlay';
  overlay.innerHTML = `
    <div class="modal-box">
      <h3 class="card-title" style="font-size:22px;">New poll</h3>
      <form class="card-form" id="poll-form">
        <input id="poll-question" placeholder="Ask a question…" required />
        <div id="poll-options-list" class="group-checklist" style="max-height:none;">
          <input class="poll-option-input" placeholder="Option 1" />
          <input class="poll-option-input" placeholder="Option 2" />
        </div>
        <button type="button" id="add-poll-option-btn" class="small-action-btn" style="align-self:flex-start;">+ Add option</button>
        <label class="checklist-item" style="border:1px solid var(--border); border-radius:8px; padding:8px;">
          <input type="checkbox" id="poll-is-quiz" />
          <span>Make this a quiz (mark the correct answer)</span>
        </label>
        <div id="quiz-answer-picker" class="hidden"></div>
        <p class="form-error hidden" id="poll-error"></p>
        <div class="modal-actions">
          <button type="button" class="modal-cancel-btn" id="poll-cancel-btn">Cancel</button>
          <button type="submit" class="btn-primary" id="poll-save-btn" style="margin-top:0;">Post</button>
        </div>
      </form>
    </div>`;
  document.body.appendChild(overlay);
  overlay.addEventListener('click', (e) => { if (e.target === overlay) overlay.remove(); });
  document.getElementById('poll-cancel-btn').addEventListener('click', () => overlay.remove());

  const optionsList = document.getElementById('poll-options-list');
  document.getElementById('add-poll-option-btn').addEventListener('click', () => {
    const count = optionsList.querySelectorAll('.poll-option-input').length;
    if (count >= 6) return;
    const input = document.createElement('input');
    input.className = 'poll-option-input';
    input.placeholder = `Option ${count + 1}`;
    optionsList.appendChild(input);
    refreshQuizAnswerPicker();
  });

  function refreshQuizAnswerPicker() {
    const picker = document.getElementById('quiz-answer-picker');
    const isQuiz = document.getElementById('poll-is-quiz').checked;
    if (!isQuiz) { picker.classList.add('hidden'); picker.innerHTML = ''; return; }
    picker.classList.remove('hidden');
    const opts = [...optionsList.querySelectorAll('.poll-option-input')].map((el, i) => ({ i, val: el.value.trim() || `Option ${i + 1}` }));
    picker.innerHTML = `<p style="font-size:12px;color:var(--ink-soft);margin:0 0 6px;">Correct answer:</p>` +
      opts.map(o => `<label class="checklist-item"><input type="radio" name="correct-option" value="${o.i}" ${o.i === 0 ? 'checked' : ''}/> <span>${escapeHtml(o.val)}</span></label>`).join('');
  }
  document.getElementById('poll-is-quiz').addEventListener('change', refreshQuizAnswerPicker);
  optionsList.addEventListener('input', refreshQuizAnswerPicker);

  document.getElementById('poll-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const errorEl = document.getElementById('poll-error');
    errorEl.classList.add('hidden');
    const question = document.getElementById('poll-question').value.trim();
    const options = [...optionsList.querySelectorAll('.poll-option-input')].map(el => el.value.trim()).filter(Boolean);
    if (!question || options.length < 2) {
      errorEl.textContent = 'Add a question and at least 2 options.';
      errorEl.classList.remove('hidden');
      return;
    }
    const isQuiz = document.getElementById('poll-is-quiz').checked;
    const correctIndex = isQuiz ? Number(document.querySelector('input[name="correct-option"]:checked')?.value || 0) : -1;

    try {
      const res = await apiCall('createPoll', {
        conversationId: activeConversationId, senderId: currentUser.userId, senderName: currentUser.name, senderPhoto: currentUser.photoURL || '',
        question, options, isQuiz, correctIndex,
      });
      conversationMessages.push(res.message);
      conversationLastTimestamp = res.message.createdAt;
      overlay.remove();
      renderChatPanel();
    } catch (err) {
      errorEl.textContent = err.message;
      errorEl.classList.remove('hidden');
    }
  });
}

function renderReplyBanner() {
  const el = document.getElementById('reply-banner');
  if (!el) return;
  if (!replyingTo) { el.innerHTML = ''; return; }
  el.innerHTML = `
    <div class="reply-banner-content">
      <span>Replying to <strong>${escapeHtml(replyingTo.senderName)}</strong>: ${escapeHtml(replyingTo.text)}</span>
      <button id="cancel-reply-btn">✕</button>
    </div>`;
  document.getElementById('cancel-reply-btn').addEventListener('click', () => { replyingTo = null; renderReplyBanner(); });
}

function attachChatHandlers() {
  attachMentionAutocomplete(document.getElementById('chat-text'));
  attachEmojiPicker(document.querySelector('#chat-form .emoji-btn'), document.getElementById('chat-text'));
  renderReplyBanner();

  let typingTimeout = null;
  document.getElementById('chat-text').addEventListener('input', () => {
    if (typingTimeout) return; // throttle — only send once per ~2s while actively typing
    apiCall('setTyping', { conversationId: activeConversationId, userId: currentUser.userId }).catch(() => {});
    typingTimeout = setTimeout(() => { typingTimeout = null; }, 2000);
  });

  document.getElementById('chat-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const input = document.getElementById('chat-text');
    const text = input.value.trim();
    if (!text) return;
    input.value = '';
    const friends = await ensureFriendsCache();
    const mentions = extractMentions(text, friends);
    const replySnapshot = replyingTo ? { messageId: replyingTo.messageId, senderName: replyingTo.senderName, text: replyingTo.text } : null;
    replyingTo = null;

    // Optimistic send — show it immediately, reconcile with the server once it responds
    const tempId = 'temp_' + Date.now();
    const tempMessage = {
      messageId: tempId, conversationId: activeConversationId, senderId: currentUser.userId,
      senderName: currentUser.name, senderPhoto: currentUser.photoURL || '', type: 'text', text,
      replyTo: JSON.stringify(replySnapshot), createdAt: new Date().toISOString(), _pending: true,
    };
    conversationMessages.push(tempMessage);
    renderChatPanel();

    try {
      const res = await apiCall('sendMessage', { conversationId: activeConversationId, senderId: currentUser.userId, senderName: currentUser.name, senderPhoto: currentUser.photoURL || '', type: 'text', text, mentions, replyTo: replySnapshot });
      const idx = conversationMessages.findIndex(m => m.messageId === tempId);
      if (idx !== -1) conversationMessages[idx] = res.message;
      conversationLastTimestamp = res.message.createdAt;
      renderChatPanel();
    } catch (err) {
      const idx = conversationMessages.findIndex(m => m.messageId === tempId);
      if (idx !== -1) { conversationMessages[idx]._pending = false; conversationMessages[idx]._failed = true; }
      renderChatPanel();
    }
  });

  document.getElementById('attach-btn').addEventListener('click', () => document.getElementById('attach-input').click());
  document.getElementById('attach-input').addEventListener('change', async (e) => {
    const file = e.target.files[0];
    if (!file) return;
    e.target.value = '';
    const type = file.type.startsWith('video') ? 'video' : 'image';

    const tempId = 'temp_' + Date.now();
    conversationMessages.push({
      messageId: tempId, conversationId: activeConversationId, senderId: currentUser.userId,
      senderName: currentUser.name, senderPhoto: currentUser.photoURL || '', type: 'text',
      text: `Uploading ${type}…`, createdAt: new Date().toISOString(), _pending: true,
    });
    renderChatPanel();

    try {
      const base64 = await fileToBase64(file);
      const res = await apiCall('sendMessage', {
        conversationId: activeConversationId, senderId: currentUser.userId, senderName: currentUser.name, senderPhoto: currentUser.photoURL || '',
        type, mediaBase64: base64, mediaMime: file.type, mediaName: file.name,
      });
      const idx = conversationMessages.findIndex(m => m.messageId === tempId);
      if (idx !== -1) conversationMessages[idx] = res.message;
      conversationLastTimestamp = res.message.createdAt;
      renderChatPanel();
    } catch (err) {
      const idx = conversationMessages.findIndex(m => m.messageId === tempId);
      if (idx !== -1) conversationMessages.splice(idx, 1);
      renderChatPanel();
      alert('Failed to send: ' + err.message);
    }
  });

  document.getElementById('rec-audio-btn').addEventListener('click', () => startRecording('audio'));
  document.getElementById('rec-video-btn').addEventListener('click', () => startRecording('video'));
  document.getElementById('poll-btn').addEventListener('click', openCreatePollModal);

  document.querySelectorAll('.poll-option:not([disabled])').forEach(btn => {
    btn.addEventListener('click', async () => {
      const messageId = btn.dataset.messageId;
      const optionIndex = Number(btn.dataset.optionIndex);
      try {
        const res = await apiCall('votePoll', { pollId: messageId, userId: currentUser.userId, optionIndex });
        const msg = conversationMessages.find(m => m.messageId === messageId);
        if (msg) { msg.pollCounts = res.results.counts; msg.pollTotalVotes = res.results.totalVotes; msg.pollMyVote = res.results.myVote; }
        renderChatPanel();
      } catch (err) { alert(err.message); }
    });
  });

  document.querySelectorAll('.reply-msg-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      replyingTo = { messageId: btn.dataset.messageId, senderName: btn.dataset.senderName, text: btn.dataset.text };
      renderReplyBanner();
      document.getElementById('chat-text').focus();
    });
  });

  document.querySelectorAll('.edit-msg-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      const messageId = btn.dataset.messageId;
      const msg = conversationMessages.find(m => m.messageId === messageId);
      const newText = prompt('Edit message:', msg?.text || '');
      if (newText === null || newText.trim() === '') return;
      try {
        await apiCall('updateMessage', { messageId, userId: currentUser.userId, text: newText.trim() });
        msg.text = newText.trim();
        renderChatPanel();
      } catch (err) { alert(err.message); }
    });
  });

  document.querySelectorAll('.delete-msg-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      if (!confirm('Delete this message?')) return;
      const messageId = btn.dataset.messageId;
      try {
        await apiCall('deleteMessage', { messageId, userId: currentUser.userId });
        conversationMessages = conversationMessages.filter(m => m.messageId !== messageId);
        renderChatPanel();
      } catch (err) { alert(err.message); }
    });
  });
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
      conversationId: activeConversationId, senderId: currentUser.userId, senderName: currentUser.name, senderPhoto: currentUser.photoURL || '',
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
    <div class="avatar-wrap">${avatarHtml(user.name, user.photoURL)}${user.userId ? onlineDotHtml(user.userId) : ''}</div>
    <div class="person-info">
      <div class="person-name">${escapeHtml(user.name)}</div>
      <div class="person-email">${escapeHtml(user.email)}</div>
    </div>
    <div class="person-action">${actionHtml}</div>
  </div>`;
}

function friendStatusActionHtml(user) {
  let primary;
  if (user.friendStatus === 'accepted') primary = `<span class="person-status">Friends</span>`;
  else if (user.friendStatus === 'pending_sent') primary = `<span class="person-status">Requested</span>`;
  else if (user.friendStatus === 'pending_received') primary = `<span class="person-status">Check requests ↓</span>`;
  else primary = `<button class="add-friend-btn" data-user-id="${user.userId}">Add friend</button>`;
  return primary + `<button class="block-user-btn" data-user-id="${user.userId}" data-user-name="${escapeHtml(user.name)}" title="Block">🚫</button>`;
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

  refreshOnlineStatus(friendsList.map(u => u.userId));

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
      cachedFriends = null;
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

  document.querySelectorAll('.block-user-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      if (!confirm(`Block ${btn.dataset.userName}? They won't appear in your feed or search.`)) return;
      try {
        await apiCall('blockUser', { blockerId: currentUser.userId, blockedId: btn.dataset.userId });
        cachedFriends = null;
        refreshPeopleData();
        const resultsBox = document.getElementById('people-search-results');
        if (resultsBox) resultsBox.innerHTML = '';
      } catch (err) { alert(err.message); }
    });
  });
}

/* ============================================================
   Inbox — direct messages + groups, opens a thread (reuses chat panel)
   ============================================================ */
function renderInboxPanel() {
  if (selectedFriend) {
    const convoId = selectedFriend.isGroup ? 'group_' + selectedFriend.userId : dmId(currentUser.userId, selectedFriend.userId);
    if (selectedFriend.isGroup) {
      loadGroupInfoThenEnter(convoId, selectedFriend);
    } else {
      activeGroupInfo = null;
      enterConversation(convoId, selectedFriend.name);
    }
    return;
  }
  loadInboxLists();
}

async function loadGroupInfoThenEnter(convoId, friendLike) {
  try {
    const res = await apiCall('getGroupDetails', { groupId: friendLike.userId });
    activeGroupInfo = res.group;
  } catch (err) {
    activeGroupInfo = null;
  }
  activeGroupCallBanner = null;
  enterConversation(convoId, friendLike.name);
  checkActiveGroupCallBanner(friendLike.userId);
}

async function checkActiveGroupCallBanner(groupId) {
  try {
    const res = await apiCall('getActiveGroupCall', { groupId });
    if (res.groupCall && !groupCallState) {
      activeGroupCallBanner = { groupCallId: res.groupCall.groupCallId, callerName: res.groupCall.callerName, type: res.groupCall.type };
      renderChatPanel();
    }
  } catch (err) { /* silent */ }
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
   Calls — WebRTC audio/video calling for DMs, signaled via
   polling the Apps Script sheet (media itself flows peer-to-peer)
   ============================================================ */
let ringAudioCtx = null;
let ringtoneInterval = null;
let ringbackInterval = null;
let incomingCallTimeout = null;

function getRingAudioCtx() {
  if (!ringAudioCtx) ringAudioCtx = new (window.AudioContext || window.webkitAudioContext)();
  if (ringAudioCtx.state === 'suspended') ringAudioCtx.resume().catch(() => {});
  return ringAudioCtx;
}

function playChime(freqs, duration, volume) {
  try {
    const ctx = getRingAudioCtx();
    const now = ctx.currentTime;
    freqs.forEach((freq) => {
      const o = ctx.createOscillator();
      const g = ctx.createGain();
      o.connect(g); g.connect(ctx.destination);
      o.type = 'sine';
      o.frequency.value = freq;
      g.gain.setValueAtTime(0.0001, now);
      g.gain.linearRampToValueAtTime(volume, now + 0.06);
      g.gain.setValueAtTime(volume, now + duration - 0.12);
      g.gain.linearRampToValueAtTime(0.0001, now + duration);
      o.start(now);
      o.stop(now + duration);
    });
  } catch (e) { /* audio not available — ignore */ }
}

// Classic two-tone phone ring, repeating
function startRingtone() {
  stopRingtone();
  playChime([950, 1400], 1.1, 0.18);
  ringtoneInterval = setInterval(() => playChime([950, 1400], 1.1, 0.18), 2200);
}
function stopRingtone() {
  if (ringtoneInterval) { clearInterval(ringtoneInterval); ringtoneInterval = null; }
}

// Softer single-tone "ringback" heard while your own call is dialing out
function startRingback() {
  stopRingback();
  playChime([440], 1.0, 0.12);
  ringbackInterval = setInterval(() => playChime([440], 1.0, 0.12), 3000);
}
function stopRingback() {
  if (ringbackInterval) { clearInterval(ringbackInterval); ringbackInterval = null; }
}

// Consolidated background poll — replaces what used to be three separate
// timers (incoming-call check, activity/notification check, presence
// heartbeat). Combining them into one request every 6s cuts background
// load roughly 3x, which is what was making the app feel sluggish.
let backgroundSyncInterval = null;

function startBackgroundSync() {
  if (backgroundSyncInterval) return;
  lastActivityCheck = new Date().toISOString(); // don't replay old activity on login
  if ('Notification' in window) {
    if (Notification.permission === 'default') {
      Notification.requestPermission();
    } else if (Notification.permission === 'denied') {
      showInAppToast('Notifications are off', 'Enable them in your browser settings to get message and comment alerts.', null);
    }
  }
  runBackgroundSync(); // fire once immediately, then on the interval
  backgroundSyncInterval = setInterval(runBackgroundSync, 6000);
}

function stopBackgroundSync() {
  if (backgroundSyncInterval) { clearInterval(backgroundSyncInterval); backgroundSyncInterval = null; }
}

async function runBackgroundSync() {
  try {
    const res = await apiCall('getBackgroundSync', { userId: currentUser.userId, since: lastActivityCheck });
    lastActivityCheck = res.checkedAt;

    if (res.call && !activeCall && !incomingCallOverlayShown) showIncomingCallOverlay(res.call);
    if (res.groupCall && !groupCallState && !activeCall && !incomingCallOverlayShown) showIncomingGroupCallOverlay(res.groupCall);

    res.items.forEach(item => {
      showActivityNotification(item);
      notificationHistory.unshift(item);
      if (notificationHistory.length > 50) notificationHistory.length = 50;
      unreadNotificationCount++;
    });
    if (res.items.length) updateBellBadge();
  } catch (err) { /* silent — background poll */ }
}

function showCallOverlay(html) {
  let overlay = document.getElementById('call-overlay');
  if (!overlay) {
    overlay = document.createElement('div');
    overlay.id = 'call-overlay';
    overlay.className = 'call-overlay';
    document.body.appendChild(overlay);
  }
  overlay.innerHTML = html;
  return overlay;
}

function hideCallOverlay() {
  const overlay = document.getElementById('call-overlay');
  if (overlay) overlay.remove();
}

function showIncomingCallOverlay(call) {
  incomingCallOverlayShown = call.callId;
  startRingtone();
  if (incomingCallTimeout) clearTimeout(incomingCallTimeout);
  incomingCallTimeout = setTimeout(() => { if (incomingCallOverlayShown === call.callId) declineIncomingCall(call); }, 30000);

  const initial = escapeHtml((call.callerName || '?')[0] || '?').toUpperCase();
  showCallOverlay(`
    <div class="call-box">
      <div class="call-avatar">${initial}</div>
      <div class="call-name">${escapeHtml(call.callerName)}</div>
      <div class="call-status">Incoming ${call.type} call…</div>
      <div class="call-actions">
        <button id="call-accept-btn" class="call-accept-btn">Accept</button>
        <button id="call-decline-btn" class="call-end-btn">Decline</button>
      </div>
    </div>`);
  document.getElementById('call-accept-btn').addEventListener('click', () => answerIncomingCall(call));
  document.getElementById('call-decline-btn').addEventListener('click', () => declineIncomingCall(call));
}

async function declineIncomingCall(call) {
  incomingCallOverlayShown = null;
  stopRingtone();
  if (incomingCallTimeout) { clearTimeout(incomingCallTimeout); incomingCallTimeout = null; }
  hideCallOverlay();
  try { await apiCall('rejectCall', { callId: call.callId }); } catch (err) { /* ignore */ }
}

async function initiateCall(calleeId, calleeName, type) {
  if (activeCall) { alert('Already in a call.'); return; }
  let localStream;
  try {
    localStream = await navigator.mediaDevices.getUserMedia({ audio: true, video: type === 'video' });
  } catch (err) {
    alert('Could not access ' + (type === 'video' ? 'camera/microphone' : 'microphone') + ': ' + err.message);
    return;
  }

  const pc = new RTCPeerConnection({ iceServers: ICE_SERVERS });
  localStream.getTracks().forEach(t => pc.addTrack(t, localStream));

  activeCall = { callId: null, role: 'caller', type, pc, localStream, remoteStream: null, seenCandidates: 0, statusInterval: null, startedAt: null, pendingCandidates: [], polling: false };

  pc.ontrack = (e) => { activeCall.remoteStream = e.streams[0]; attachRemoteStreamIfReady(); };
  pc.oniceconnectionstatechange = () => {
    if (pc.iceConnectionState === 'failed' && activeCall) {
      showCallEndedMessage('Connection failed — check your network and try again.');
    }
  };
  // ICE gathering starts as soon as setLocalDescription() runs below — well
  // before startCall() resolves with a callId. Candidates that arrive in that
  // window are queued here instead of being silently dropped.
  pc.onicecandidate = (e) => {
    if (!e.candidate || !activeCall) return;
    if (activeCall.callId) {
      apiCall('addIceCandidate', { callId: activeCall.callId, role: 'caller', candidate: e.candidate.toJSON() }).catch(() => {});
    } else {
      activeCall.pendingCandidates.push(e.candidate.toJSON());
    }
  };

  renderOutgoingCallUI(calleeName, type);

  const offer = await pc.createOffer();
  await pc.setLocalDescription(offer);

  try {
    const res = await apiCall('startCall', {
      conversationId: dmId(currentUser.userId, calleeId),
      callerId: currentUser.userId, callerName: currentUser.name,
      calleeId, calleeName, type, offerSDP: offer,
    });
    activeCall.callId = res.callId;
    // flush any candidates gathered before we had a callId to send them with
    const queued = activeCall.pendingCandidates.splice(0, activeCall.pendingCandidates.length);
    queued.forEach(c => apiCall('addIceCandidate', { callId: activeCall.callId, role: 'caller', candidate: c }).catch(() => {}));
    startRingback();
  } catch (err) {
    alert('Could not start call: ' + err.message);
    hangupCall();
    return;
  }

  activeCall.statusInterval = setInterval(() => pollOutgoingCall(calleeName, type), 1500);
}

async function pollOutgoingCall(calleeName, type) {
  if (!activeCall || !activeCall.callId || activeCall.polling) return; // skip if the previous poll hasn't finished yet
  activeCall.polling = true;
  try {
    const res = await apiCall('getCall', { callId: activeCall.callId });
    const call = res.call;
    if (!call || !activeCall) return;

    if (call.status === 'accepted' && !activeCall.pc.currentRemoteDescription) {
      stopRingback();
      await activeCall.pc.setRemoteDescription(new RTCSessionDescription(call.answerSDP));
      activeCall.startedAt = Date.now();
      renderActiveCallUI(calleeName, type);
    }
    if (call.status === 'rejected') { stopRingback(); showCallEndedMessage(calleeName + ' declined the call.'); return; }
    if (call.status === 'ended') { stopRingback(); showCallEndedMessage('Call ended.'); return; }

    // add any new candidates from the callee side — each wrapped individually
    // so one bad/duplicate candidate can't block the rest from this batch
    const newOnes = call.calleeCandidates.slice(activeCall.seenCandidates);
    for (const c of newOnes) { try { await activeCall.pc.addIceCandidate(c); } catch (e) { /* ignore malformed/duplicate */ } }
    activeCall.seenCandidates = call.calleeCandidates.length;
  } catch (err) {
    /* network hiccup on this poll — next tick will retry */
  } finally {
    if (activeCall) activeCall.polling = false;
  }
}

async function answerIncomingCall(call) {
  incomingCallOverlayShown = null;
  stopRingtone();
  if (incomingCallTimeout) { clearTimeout(incomingCallTimeout); incomingCallTimeout = null; }
  let localStream;
  try {
    localStream = await navigator.mediaDevices.getUserMedia({ audio: true, video: call.type === 'video' });
  } catch (err) {
    alert('Could not access ' + (call.type === 'video' ? 'camera/microphone' : 'microphone') + ': ' + err.message);
    try { await apiCall('rejectCall', { callId: call.callId }); } catch (e) {}
    hideCallOverlay();
    return;
  }

  const pc = new RTCPeerConnection({ iceServers: ICE_SERVERS });
  localStream.getTracks().forEach(t => pc.addTrack(t, localStream));

  activeCall = { callId: call.callId, role: 'callee', type: call.type, pc, localStream, remoteStream: null, seenCandidates: 0, statusInterval: null, startedAt: Date.now(), polling: false };

  pc.ontrack = (e) => { activeCall.remoteStream = e.streams[0]; attachRemoteStreamIfReady(); };
  pc.oniceconnectionstatechange = () => {
    if (pc.iceConnectionState === 'failed' && activeCall) {
      showCallEndedMessage('Connection failed — check your network and try again.');
    }
  };
  pc.onicecandidate = (e) => {
    if (e.candidate && activeCall) {
      apiCall('addIceCandidate', { callId: call.callId, role: 'callee', candidate: e.candidate.toJSON() }).catch(() => {});
    }
  };

  await pc.setRemoteDescription(new RTCSessionDescription(call.offerSDP));
  const answer = await pc.createAnswer();
  await pc.setLocalDescription(answer);
  await apiCall('answerCall', { callId: call.callId, answerSDP: answer });

  renderActiveCallUI(call.callerName, call.type);
  activeCall.statusInterval = setInterval(() => pollActiveCallForHangupAndCandidates(call.callerName), 1500);
}

async function pollActiveCallForHangupAndCandidates() {
  if (!activeCall || !activeCall.callId || activeCall.polling) return;
  activeCall.polling = true;
  try {
    const res = await apiCall('getCall', { callId: activeCall.callId });
    const call = res.call;
    if (!call || !activeCall) return;
    if (call.status === 'ended') { showCallEndedMessage('Call ended.'); return; }

    const newOnes = call.callerCandidates.slice(activeCall.seenCandidates);
    for (const c of newOnes) { try { await activeCall.pc.addIceCandidate(c); } catch (e) { /* ignore malformed/duplicate */ } }
    activeCall.seenCandidates = call.callerCandidates.length;
  } catch (err) {
    /* network hiccup on this poll — next tick will retry */
  } finally {
    if (activeCall) activeCall.polling = false;
  }
}

function attachRemoteStreamIfReady() {
  if (!activeCall || !activeCall.remoteStream) return;
  const remoteVideo = document.getElementById('remote-video');
  const remoteAudio = document.getElementById('remote-audio');
  if (remoteVideo) { remoteVideo.srcObject = activeCall.remoteStream; remoteVideo.play().catch(() => {}); }
  if (remoteAudio) { remoteAudio.srcObject = activeCall.remoteStream; remoteAudio.play().catch(() => {}); }
}

function renderOutgoingCallUI(name, type) {
  const initial = escapeHtml((name || '?')[0] || '?').toUpperCase();
  showCallOverlay(`
    <div class="call-box">
      <div class="call-avatar">${initial}</div>
      <div class="call-name">${escapeHtml(name)}</div>
      <div class="call-status">Calling…</div>
      <button id="call-cancel-btn" class="call-end-btn">End</button>
    </div>`);
  document.getElementById('call-cancel-btn').addEventListener('click', hangupCall);
}

function renderActiveCallUI(name, type) {
  if (type === 'video') {
    showCallOverlay(`
      <div class="call-box call-box-video">
        <video id="remote-video" autoplay playsinline muted class="remote-video"></video>
        <audio id="remote-audio" autoplay></audio>
        <video id="local-video" autoplay playsinline muted class="local-video"></video>
        <div class="call-controls">
          <button id="call-hangup-btn" class="call-end-btn">End call</button>
        </div>
      </div>`);
    document.getElementById('local-video').srcObject = activeCall.localStream;
  } else {
    const initial = escapeHtml((name || '?')[0] || '?').toUpperCase();
    showCallOverlay(`
      <div class="call-box">
        <audio id="remote-audio" autoplay></audio>
        <div class="call-avatar">${initial}</div>
        <div class="call-name">${escapeHtml(name)}</div>
        <div class="call-status">Connected</div>
        <button id="call-hangup-btn" class="call-end-btn">End call</button>
      </div>`);
  }
  document.getElementById('call-hangup-btn').addEventListener('click', hangupCall);
  attachRemoteStreamIfReady();
}

function showCallEndedMessage(message) {
  const box = document.querySelector('.call-box');
  if (box) {
    box.innerHTML = `<div class="call-status">${escapeHtml(message)}</div>`;
  }
  cleanupCall();
  setTimeout(hideCallOverlay, 1800);
}

function hangupCall() {
  if (activeCall && activeCall.callId) {
    apiCall('endCall', { callId: activeCall.callId }).catch(() => {});
  }
  cleanupCall();
  hideCallOverlay();
}

function cleanupCall() {
  stopRingtone();
  stopRingback();
  if (activeCall) {
    if (activeCall.statusInterval) clearInterval(activeCall.statusInterval);
    if (activeCall.pc) activeCall.pc.close();
    if (activeCall.localStream) activeCall.localStream.getTracks().forEach(t => t.stop());
  }
  activeCall = null;
}

/* ============================================================
   Group calls — mesh WebRTC (each participant connects directly
   to every other participant). Signaling relayed via the sheet.
   ============================================================ */
let groupCallState = null; // { groupCallId, groupId, groupName, type, localStream, peers: {userId:{pc,remoteStream,userName,userPhoto}}, signalInterval, participantsInterval, lastSignalCheck, muted, videoOff }

async function startGroupVideoCall(groupId, groupName, type) {
  if (groupCallState || activeCall) { alert('Already in a call.'); return; }
  let localStream;
  try {
    localStream = await navigator.mediaDevices.getUserMedia({ audio: true, video: type === 'video' });
  } catch (err) {
    alert('Could not access ' + (type === 'video' ? 'camera/microphone' : 'microphone') + ': ' + err.message);
    return;
  }
  try {
    const res = await apiCall('startGroupCall', { groupId, callerId: currentUser.userId, callerName: currentUser.name, callerPhoto: currentUser.photoURL || '', type });
    beginGroupCallSession(res.groupCall.groupCallId, groupId, groupName, type, localStream);
  } catch (err) {
    alert('Could not start call: ' + err.message);
    localStream.getTracks().forEach(t => t.stop());
  }
}

async function joinGroupCallFlow(groupCallId, groupId, groupName, type) {
  if (groupCallState || activeCall) { alert('Already in a call.'); return; }
  let localStream;
  try {
    localStream = await navigator.mediaDevices.getUserMedia({ audio: true, video: type === 'video' });
  } catch (err) {
    alert('Could not access ' + (type === 'video' ? 'camera/microphone' : 'microphone') + ': ' + err.message);
    return;
  }
  try {
    await apiCall('joinGroupCall', { groupCallId, userId: currentUser.userId, userName: currentUser.name, userPhoto: currentUser.photoURL || '' });
    beginGroupCallSession(groupCallId, groupId, groupName, type, localStream);

    const res = await apiCall('getGroupCallParticipants', { groupCallId });
    res.participants.forEach(p => {
      if (p.userId === currentUser.userId) return;
      connectToGroupPeer(p.userId, p.userName, p.userPhoto, true);
    });
  } catch (err) {
    alert('Could not join call: ' + err.message);
    localStream.getTracks().forEach(t => t.stop());
  }
}

function beginGroupCallSession(groupCallId, groupId, groupName, type, localStream) {
  groupCallState = {
    groupCallId, groupId, groupName, type, localStream, peers: {},
    signalInterval: null, participantsInterval: null, lastSignalCheck: new Date().toISOString(),
    muted: false, videoOff: false, signalPolling: false, participantsPolling: false,
  };
  renderGroupCallUI();
  groupCallState.signalInterval = setInterval(pollGroupSignals, 1500);
  groupCallState.participantsInterval = setInterval(pollGroupParticipants, 4000);
}

function connectToGroupPeer(peerId, peerName, peerPhoto, isInitiator) {
  if (!groupCallState || groupCallState.peers[peerId]) return;
  const pc = new RTCPeerConnection({ iceServers: ICE_SERVERS });
  groupCallState.localStream.getTracks().forEach(t => pc.addTrack(t, groupCallState.localStream));

  const peer = { pc, remoteStream: null, userName: peerName, userPhoto: peerPhoto, candidateQueue: [] };
  groupCallState.peers[peerId] = peer;

  pc.ontrack = (e) => { peer.remoteStream = e.streams[0]; renderGroupCallUI(); };
  pc.onicecandidate = (e) => {
    if (e.candidate) {
      apiCall('sendGroupSignal', { groupCallId: groupCallState.groupCallId, fromUserId: currentUser.userId, toUserId: peerId, signalType: 'ice', payload: e.candidate.toJSON() }).catch(() => {});
    }
  };
  // helps spot connections that never establish, instead of failing silently
  pc.oniceconnectionstatechange = () => {
    if (['failed', 'disconnected'].includes(pc.iceConnectionState) && groupCallState) renderGroupCallUI();
  };

  if (isInitiator) {
    pc.createOffer().then(async (offer) => {
      await pc.setLocalDescription(offer);
      apiCall('sendGroupSignal', { groupCallId: groupCallState.groupCallId, fromUserId: currentUser.userId, toUserId: peerId, signalType: 'offer', payload: offer }).catch(() => {});
    });
  }
  renderGroupCallUI();
}

async function addGroupIceCandidate(peer, candidate) {
  // queue it if the remote description isn't set yet — adding too early throws
  // and the candidate would otherwise be silently lost, breaking connectivity
  if (!peer.pc.remoteDescription || !peer.pc.remoteDescription.type) {
    peer.candidateQueue.push(candidate);
    return;
  }
  try { await peer.pc.addIceCandidate(candidate); } catch (e) { /* ignore malformed/duplicate candidates */ }
}

async function flushGroupCandidateQueue(peer) {
  const queued = peer.candidateQueue.splice(0, peer.candidateQueue.length);
  for (const c of queued) {
    try { await peer.pc.addIceCandidate(c); } catch (e) { /* ignore */ }
  }
}

async function pollGroupSignals() {
  if (!groupCallState || groupCallState.signalPolling) return; // skip if the previous poll hasn't finished yet
  groupCallState.signalPolling = true;
  try {
    const res = await apiCall('getGroupSignals', { groupCallId: groupCallState.groupCallId, userId: currentUser.userId, since: groupCallState.lastSignalCheck });
    groupCallState.lastSignalCheck = res.checkedAt;
    for (const sig of res.signals) {
      // each signal is isolated — one bad/duplicate/out-of-order signal
      // must not block the rest of this batch from being processed
      try {
        let peer = groupCallState.peers[sig.fromUserId];
        if (sig.signalType === 'offer') {
          if (!peer) { connectToGroupPeer(sig.fromUserId, sig.fromUserId, '', false); peer = groupCallState.peers[sig.fromUserId]; }
          await peer.pc.setRemoteDescription(new RTCSessionDescription(sig.payload));
          await flushGroupCandidateQueue(peer);
          const answer = await peer.pc.createAnswer();
          await peer.pc.setLocalDescription(answer);
          apiCall('sendGroupSignal', { groupCallId: groupCallState.groupCallId, fromUserId: currentUser.userId, toUserId: sig.fromUserId, signalType: 'answer', payload: answer }).catch(() => {});
        } else if (sig.signalType === 'answer' && peer) {
          if (!peer.pc.currentRemoteDescription) {
            await peer.pc.setRemoteDescription(new RTCSessionDescription(sig.payload));
            await flushGroupCandidateQueue(peer);
          }
        } else if (sig.signalType === 'ice' && peer) {
          await addGroupIceCandidate(peer, sig.payload);
        }
      } catch (sigErr) { /* this specific signal failed — move on to the next one */ }
    }
  } catch (err) { /* silent — background poll, next tick retries */ }
  finally { if (groupCallState) groupCallState.signalPolling = false; }
}

async function pollGroupParticipants() {
  if (!groupCallState || groupCallState.participantsPolling) return;
  groupCallState.participantsPolling = true;
  try {
    const res = await apiCall('getGroupCallParticipants', { groupCallId: groupCallState.groupCallId });
    const activeIds = res.participants.map(p => p.userId);
    // connect to anyone new
    res.participants.forEach(p => {
      if (p.userId === currentUser.userId || groupCallState.peers[p.userId]) return;
      connectToGroupPeer(p.userId, p.userName, p.userPhoto, true);
    });
    // tear down anyone who left
    Object.keys(groupCallState.peers).forEach(peerId => {
      if (activeIds.indexOf(peerId) === -1) {
        groupCallState.peers[peerId].pc.close();
        delete groupCallState.peers[peerId];
      }
    });
    renderGroupCallUI();
  } catch (err) { /* silent */ }
  finally { if (groupCallState) groupCallState.participantsPolling = false; }
}

function renderGroupCallUI() {
  if (!groupCallState) { hideCallOverlay(); return; }
  const isVideo = groupCallState.type === 'video';
  const peerTiles = Object.entries(groupCallState.peers).map(([id, p]) => groupCallTileHtml(p.userName, p.userPhoto, p.remoteStream, isVideo, id)).join('');
  const selfTile = groupCallTileHtml(currentUser.name + ' (you)', currentUser.photoURL, groupCallState.localStream, isVideo && !groupCallState.videoOff, 'self', true);

  showCallOverlay(`
    <div class="group-call-box">
      <div class="group-call-header">${escapeHtml(groupCallState.groupName)}</div>
      <div class="group-call-grid">${selfTile}${peerTiles}</div>
      <div class="group-call-controls">
        <button id="gc-mute-btn">${groupCallState.muted ? '🔇 Unmute' : '🎤 Mute'}</button>
        ${isVideo ? `<button id="gc-video-btn">${groupCallState.videoOff ? '📷 Camera on' : '📷 Camera off'}</button>` : ''}
        <button id="gc-leave-btn" class="call-end-btn">Leave</button>
      </div>
    </div>`);

  document.querySelectorAll('.group-call-tile video, .group-call-tile audio').forEach(el => {
    const stream = el.dataset.streamOwner === 'self' ? groupCallState.localStream : (groupCallState.peers[el.dataset.streamOwner] || {}).remoteStream;
    if (stream && el.srcObject !== stream) {
      el.srcObject = stream;
      el.play().catch(() => { /* will retry once the user interacts again if autoplay is blocked */ });
    }
  });

  document.getElementById('gc-mute-btn').addEventListener('click', toggleGroupCallMute);
  const videoBtn = document.getElementById('gc-video-btn');
  if (videoBtn) videoBtn.addEventListener('click', toggleGroupCallVideo);
  document.getElementById('gc-leave-btn').addEventListener('click', leaveGroupCallFlow);
}

function groupCallTileHtml(name, photo, stream, showVideo, ownerId, isSelf) {
  const hasVideoTrack = stream && showVideo;
  // Audio is always played through its own dedicated element, decoupled from
  // whether video is shown — previously, if a peer's camera was off (or the
  // stream hadn't arrived at render time), there was no playback element at
  // all for them, so their audio silently never played.
  const audioEl = (!isSelf && stream) ? `<audio autoplay data-stream-owner="${ownerId}" style="display:none;"></audio>` : '';
  return `
    <div class="group-call-tile">
      ${hasVideoTrack
        ? `<video autoplay playsinline muted data-stream-owner="${ownerId}"></video>`
        : `<div class="group-call-avatar">${avatarHtml(name, photo, 64)}</div>`}
      ${audioEl}
      <div class="group-call-name">${escapeHtml(name)}</div>
    </div>`;
}

function toggleGroupCallMute() {
  if (!groupCallState) return;
  groupCallState.muted = !groupCallState.muted;
  groupCallState.localStream.getAudioTracks().forEach(t => t.enabled = !groupCallState.muted);
  renderGroupCallUI();
}

function toggleGroupCallVideo() {
  if (!groupCallState) return;
  groupCallState.videoOff = !groupCallState.videoOff;
  groupCallState.localStream.getVideoTracks().forEach(t => t.enabled = !groupCallState.videoOff);
  renderGroupCallUI();
}

async function leaveGroupCallFlow() {
  if (!groupCallState) return;
  const groupCallId = groupCallState.groupCallId;
  clearInterval(groupCallState.signalInterval);
  clearInterval(groupCallState.participantsInterval);
  Object.values(groupCallState.peers).forEach(p => p.pc.close());
  groupCallState.localStream.getTracks().forEach(t => t.stop());
  groupCallState = null;
  hideCallOverlay();
  try { await apiCall('leaveGroupCall', { groupCallId, userId: currentUser.userId }); } catch (err) { /* ignore */ }
}

function showIncomingGroupCallOverlay(call) {
  if (groupCallState || activeCall || incomingCallOverlayShown) return; // already busy
  incomingCallOverlayShown = call.groupCallId;
  startRingtone();
  const declineTimeout = setTimeout(() => { if (incomingCallOverlayShown === call.groupCallId) declineGroupCall(call); }, 30000);

  showCallOverlay(`
    <div class="call-box">
      <div class="call-avatar">👥</div>
      <div class="call-name">${escapeHtml(call.groupName)}</div>
      <div class="call-status">${escapeHtml(call.callerName)} started a ${call.type} call…</div>
      <div class="call-actions">
        <button id="gc-accept-btn" class="call-accept-btn">Join</button>
        <button id="gc-decline-btn" class="call-end-btn">Decline</button>
      </div>
    </div>`);
  document.getElementById('gc-accept-btn').addEventListener('click', () => {
    clearTimeout(declineTimeout);
    incomingCallOverlayShown = null;
    stopRingtone();
    joinGroupCallFlow(call.groupCallId, call.groupId, call.groupName, call.type);
  });
  document.getElementById('gc-decline-btn').addEventListener('click', () => { clearTimeout(declineTimeout); declineGroupCall(call); });
}

async function declineGroupCall(call) {
  incomingCallOverlayShown = null;
  stopRingtone();
  hideCallOverlay();
  try { await apiCall('leaveGroupCall', { groupCallId: call.groupCallId, userId: currentUser.userId }); } catch (err) { /* ignore */ }
}

async function openManageGroupModal() {
  const existing = document.getElementById('manage-group-overlay');
  if (existing) existing.remove();

  const overlay = document.createElement('div');
  overlay.id = 'manage-group-overlay';
  overlay.className = 'modal-overlay';
  overlay.innerHTML = `
    <div class="modal-box">
      <h3 class="card-title" style="font-size:22px;">Manage "${escapeHtml(activeGroupInfo.name)}"</h3>
      <section class="people-section">
        <h3>Members</h3>
        <div id="manage-current-members"><p class="post-time">Loading…</p></div>
      </section>
      <section class="people-section">
        <h3>Add friends</h3>
        <div id="manage-addable-friends"><p class="post-time">Loading…</p></div>
      </section>
      <div class="modal-actions">
        <button type="button" class="modal-cancel-btn" id="manage-close-btn">Close</button>
      </div>
    </div>`;
  document.body.appendChild(overlay);
  overlay.addEventListener('click', (e) => { if (e.target === overlay) overlay.remove(); });
  document.getElementById('manage-close-btn').addEventListener('click', () => overlay.remove());

  await refreshManageGroupModal();
}

async function refreshManageGroupModal() {
  const overlay = document.getElementById('manage-group-overlay');
  if (!overlay) return;

  const res = await apiCall('getGroupDetails', { groupId: activeGroupInfo.groupId });
  activeGroupInfo = res.group;

  const membersBox = document.getElementById('manage-current-members');
  if (membersBox) {
    membersBox.innerHTML = activeGroupInfo.members.map(m => {
      const isCreator = m.userId === activeGroupInfo.createdBy;
      const action = isCreator
        ? `<span class="person-status">Creator</span>`
        : `<button class="remove-member-btn" data-user-id="${m.userId}">Remove</button>`;
      return personCardHtml(m, action);
    }).join('');
    membersBox.querySelectorAll('.remove-member-btn').forEach(btn => {
      btn.addEventListener('click', async () => {
        btn.disabled = true; btn.textContent = 'Removing…';
        try {
          await apiCall('removeGroupMember', { groupId: activeGroupInfo.groupId, requesterId: currentUser.userId, userId: btn.dataset.userId });
          await refreshManageGroupModal();
        } catch (err) { alert(err.message); }
      });
    });
  }

  const friendsRes = await apiCall('getFriends', { userId: currentUser.userId });
  const addableBox = document.getElementById('manage-addable-friends');
  if (addableBox) {
    const memberIds = activeGroupInfo.memberIds;
    const addable = friendsRes.friends.filter(f => memberIds.indexOf(f.userId) === -1);
    addableBox.innerHTML = addable.length
      ? addable.map(f => personCardHtml(f, `<button class="add-member-btn" data-user-id="${f.userId}">Add</button>`)).join('')
      : '<p class="empty-state">All your friends are already in this group.</p>';
    addableBox.querySelectorAll('.add-member-btn').forEach(btn => {
      btn.addEventListener('click', async () => {
        btn.disabled = true; btn.textContent = 'Adding…';
        try {
          await apiCall('addGroupMember', { groupId: activeGroupInfo.groupId, requesterId: currentUser.userId, userId: btn.dataset.userId });
          await refreshManageGroupModal();
        } catch (err) { alert(err.message); }
      });
    });
  }
}

/* ============================================================
   Presence — online status lookups (heartbeat itself is sent as
   part of the consolidated background sync poll, not separately)
   ============================================================ */
async function refreshOnlineStatus(userIds) {
  if (!userIds.length) return;
  try {
    const res = await apiCall('getOnlineStatus', { userIds });
    Object.assign(onlineStatusMap, res.status);
    document.querySelectorAll('[data-online-for]').forEach(dot => {
      dot.classList.toggle('online', !!onlineStatusMap[dot.dataset.onlineFor]);
    });
  } catch (err) { /* silent */ }
}

function onlineDotHtml(userId) {
  return `<span class="online-dot ${onlineStatusMap[userId] ? 'online' : ''}" data-online-for="${userId}"></span>`;
}

/* ============================================================
   Notification bell state (the actual polling now happens inside
   the consolidated runBackgroundSync)
   ============================================================ */
let lastActivityCheck = null;

function updateBellBadge() {
  const btn = document.getElementById('bell-btn');
  if (!btn) return;
  btn.innerHTML = `🔔${unreadNotificationCount > 0 ? `<span class="bell-badge">${unreadNotificationCount > 9 ? '9+' : unreadNotificationCount}</span>` : ''}`;
}

function toggleBellDropdown() {
  const existing = document.getElementById('bell-dropdown');
  if (existing) { existing.remove(); return; }

  unreadNotificationCount = 0;
  updateBellBadge();

  const dropdown = document.createElement('div');
  dropdown.id = 'bell-dropdown';
  dropdown.className = 'bell-dropdown';
  dropdown.innerHTML = notificationHistory.length
    ? notificationHistory.map(item => `
        <div class="bell-item">
          <strong>${escapeHtml(item.title)}</strong>
          <div>${escapeHtml((item.body || '').slice(0, 80))}</div>
        </div>`).join('')
    : '<p class="empty-state">No notifications yet.</p>';
  document.getElementById('bell-btn').parentElement.style.position = 'relative';
  document.getElementById('bell-btn').parentElement.appendChild(dropdown);

  dropdown.querySelectorAll('.bell-item').forEach((el, i) => {
    el.addEventListener('click', () => { handleActivityClick(notificationHistory[i]); dropdown.remove(); });
  });

  setTimeout(() => {
    document.addEventListener('click', function handler(ev) {
      if (!dropdown.contains(ev.target) && ev.target.id !== 'bell-btn') { dropdown.remove(); document.removeEventListener('click', handler); }
    });
  }, 0);
}

function playNotificationSound() {
  try {
    const ctx = new (window.AudioContext || window.webkitAudioContext)();
    const o = ctx.createOscillator();
    const g = ctx.createGain();
    o.connect(g); g.connect(ctx.destination);
    o.frequency.value = 880;
    g.gain.setValueAtTime(0.15, ctx.currentTime);
    g.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + 0.35);
    o.start(); o.stop(ctx.currentTime + 0.35);
  } catch (e) { /* audio not available — ignore */ }
}

function showActivityNotification(item) {
  playNotificationSound();
  const title = item.title || 'New activity';
  const body = (item.body || '').slice(0, 100);
  if ('Notification' in window && Notification.permission === 'granted') {
    try {
      const n = new Notification(title, { body });
      n.onclick = () => { window.focus(); handleActivityClick(item); };
    } catch (e) { /* ignore */ }
  }
  showInAppToast(title, body, item);
}

function showInAppToast(title, body, item) {
  const toast = document.createElement('div');
  toast.className = 'toast-notification';
  toast.innerHTML = `<strong>${escapeHtml(title)}</strong><div>${escapeHtml(body)}</div>`;
  if (item) toast.addEventListener('click', () => { handleActivityClick(item); toast.remove(); });
  else toast.addEventListener('click', () => toast.remove());
  document.body.appendChild(toast);
  setTimeout(() => toast.remove(), 6000);
}

function handleActivityClick(item) {
  if (!item) return;
  if ((item.type === 'dm_message' || item.type === 'mention_message') && item.partnerId) {
    currentTab = 'inbox';
    selectedFriend = { userId: item.partnerId, name: item.partnerName };
  } else if ((item.type === 'group_message' || item.type === 'mention_message') && item.groupId) {
    currentTab = 'inbox';
    selectedFriend = { userId: item.groupId, name: item.groupName, isGroup: true };
  } else if (item.type === 'mention_post' || item.type === 'mention_comment' || item.type === 'comment_on_post' || item.type === 'friend_story') {
    currentTab = 'feed';
    selectedFriend = null;
  } else {
    return;
  }
  render();
}

/* ============================================================
   Profile modal — edit name / bio / photo
   ============================================================ */
async function loadBlockedUsersList() {
  const res = await apiCall('getBlockedUsers', { userId: currentUser.userId });
  const box = document.getElementById('blocked-users-list');
  if (!box) return;
  box.innerHTML = res.users.length
    ? res.users.map(u => personCardHtml(u, `<button class="unblock-user-btn" data-user-id="${u.userId}">Unblock</button>`)).join('')
    : '<p class="empty-state">No blocked users.</p>';
  box.querySelectorAll('.unblock-user-btn').forEach(btn => {
    btn.addEventListener('click', async () => {
      await apiCall('unblockUser', { blockerId: currentUser.userId, blockedId: btn.dataset.userId });
      loadBlockedUsersList();
    });
  });
}

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
      <section class="people-section" style="margin-top:18px;">
        <h3>Blocked users</h3>
        <div id="blocked-users-list"><p class="post-time">Loading…</p></div>
      </section>
    </div>`;
  document.body.appendChild(overlay);
  loadBlockedUsersList();

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
   Pause background polling while the tab is hidden — avoids
   wasted requests and makes things feel snappier when you come back
   ============================================================ */
document.addEventListener('visibilitychange', () => {
  if (!currentUser) return;
  if (document.hidden) {
    stopFeedPolling();
    stopBackgroundSync();
  } else {
    startBackgroundSync();
    if (currentTab === 'feed') startFeedPolling();
  }
});

/* ============================================================
   Boot
   ============================================================ */
render();
setTimeout(() => {
  const splash = document.getElementById('splash-screen');
  if (splash) splash.classList.add('splash-hidden');
  setTimeout(() => splash?.remove(), 600);
}, 1100);
</script>
</body>
</html>
