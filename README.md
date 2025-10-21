# ansh-portfolio
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Ansh Singh — Student Developer</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#050507;
      --card:#0b0c10;
      --muted:#9aa0a6;
      --accent1: linear-gradient(135deg,#7b61ff 0%,#00d0ff 100%);
      --glow: 0 10px 30px rgba(124,85,255,0.14), 0 2px 8px rgba(0,208,255,0.06);
      --glass: rgba(255,255,255,0.03);
    }
    *{box-sizing:border-box}
    html,body{height:100%;background:var(--bg);font-family:'Inter',system-ui,Arial;margin:0;color:#e6eef8}
    a{color:inherit}
    .container{max-width:1000px;margin:40px auto;padding:24px}

    /* Header / Hero */
    header{display:flex;align-items:center;justify-content:space-between;gap:16px}
    .logo{display:flex;align-items:center;gap:12px}
    .logo .mark{width:46px;height:46px;border-radius:10px;background:linear-gradient(135deg,#7b61ff,#00d0ff);display:flex;align-items:center;justify-content:center;font-weight:800;color:#050507}
    .nav{display:flex;gap:18px;align-items:center}
    .nav a{padding:8px 12px;border-radius:8px;color:var(--muted);text-decoration:none;font-weight:600}
    .nav a:hover{background:var(--glass);color:#fff}

    .hero{display:grid;grid-template-columns:1fr 380px;gap:28px;align-items:center;margin-top:36px}
    .intro h1{font-size:34px;margin:0 0 6px 0;line-height:1.05}
    .intro .title{font-weight:600;color:linear-gradient(90deg,#fff,#d3e9ff)}
    .typing{color:#a8c9ff;font-weight:600}
    .bio{margin-top:14px;color:var(--muted);max-width:62%}
    .cta{margin-top:18px;display:flex;gap:10px}
    .btn{padding:10px 16px;border-radius:10px;background:linear-gradient(90deg,#7b61ff,#00d0ff);color:#050507;font-weight:700;text-decoration:none;box-shadow:var(--glow);border:none;cursor:pointer}
    .btn.outline{background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--muted)}

    /* Card (right) */
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:18px;border-radius:12px;box-shadow:var(--glow)}
    .quick{display:flex;flex-direction:column;gap:12px}
    .stat{display:flex;justify-content:space-between;align-items:center}
    .small{color:var(--muted);font-weight:600}

    /* Sections */
    section{margin-top:46px}
    .grid-3{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}

    /* Skills */
    .skill{background:var(--card);padding:14px;border-radius:10px}
    .skill .name{display:flex;justify-content:space-between;margin-bottom:8px;color:var(--muted);font-weight:700}
    .bar{height:10px;background:#0a0b0e;border-radius:999px;overflow:hidden}
    .bar > i{display:block;height:100%;background:linear-gradient(90deg,#7b61ff,#00d0ff);width:0%;border-radius:999px;transition:width 1.2s ease}

    /* Projects */
    .project{background:linear-gradient(180deg,rgba(255,255,255,0.01),transparent);padding:16px;border-radius:12px;cursor:pointer;transform:translateY(0);transition:transform .25s ease,box-shadow .25s ease}
    .project:hover{transform:translateY(-8px);box-shadow:var(--glow)}
    .proj-head{display:flex;justify-content:space-between;align-items:center}
    .chip{font-weight:700;padding:6px 10px;border-radius:999px;background:rgba(255,255,255,0.03);color:var(--muted);font-size:13px}

    /* Footer / Contact */
    .contact{display:flex;gap:16px;align-items:center}
    .icon{width:42px;height:42px;border-radius:10px;background:linear-gradient(135deg,#141318,#121217);display:flex;align-items:center;justify-content:center}

    /* Popup modal */
    .modal{position:fixed;inset:0;background:rgba(2,2,6,0.6);display:none;align-items:center;justify-content:center;padding:24px}
    .modal.open{display:flex}
    .modal .inner{background:#06060a;padding:22px;border-radius:12px;max-width:760px;width:100%;box-shadow:0 30px 80px rgba(0,0,0,0.6)}
    .modal h3{margin:0 0 8px 0}
    .modal .meta{color:var(--muted);font-size:14px;margin-bottom:14px}

    /* tiny floating decor */
    .float-blob{position:fixed;right:-120px;top:120px;width:300px;height:300px;border-radius:50%;filter:blur(60px);opacity:.6;background:radial-gradient(circle at 20% 20%, rgba(123,97,255,0.35), transparent 20%), radial-gradient(circle at 80% 80%, rgba(0,208,255,0.25), transparent 20%)}

    /* responsive */
    @media (max-width:900px){
      .hero{grid-template-columns:1fr}
      .grid-3{grid-template-columns:repeat(2,1fr)}
    }
    @media (max-width:520px){.grid-3{grid-template-columns:1fr}.intro h1{font-size:26px}.container{padding:14px;margin:18px auto}}

    /* animations */
    .slide-up{opacity:0;transform:translateY(12px);transition:opacity .7s ease,transform .7s ease}
    .slide-up.visible{opacity:1;transform:none}

    /* typing */
    .typing-wrap{display:inline-block;height:28px;vertical-align:middle;overflow:hidden}
    .typing-text{display:inline-block;white-space:nowrap;animation:typing 3.6s steps(30,end) infinite}
    @keyframes typing{0%{transform:translateX(0)}49%{transform:translateX(0)}51%{transform:translateX(-100%)}100%{transform:translateX(-100%)}}

    /* small neat form */
    input[type="text"],textarea{width:100%;padding:10px;border-radius:8px;background:#08080b;border:1px solid rgba(255,255,255,0.03);color:#dfefff}
    button.send{background:linear-gradient(90deg,#7b61ff,#00d0ff);border:none;padding:10px 14px;border-radius:10px;color:#050507;font-weight:700}

  </style>
</head>
<body>
  <div class="float-blob" aria-hidden></div>
  <div class="container">
    <header>
      <div class="logo">
        <div class="mark">AS</div>
        <div>
          <div style="font-weight:800">Ansh Singh</div>
          <div style="font-size:13px;color:var(--muted);margin-top:3px">Student Developer • Class 11</div>
        </div>
      </div>
      <nav class="nav">
        <a href="#projects">Projects</a>
        <a href="#skills">Skills</a>
        <a href="#contact">Contact</a>
      </nav>
    </header>

    <main class="hero">
      <div class="intro">
        <h1 class="slide-up visible">Hi, I’m <span style="background:linear-gradient(90deg,#fff,#d3e9ff);-webkit-background-clip:text;background-clip:text;color:transparent;font-weight:900">Ansh Singh</span></h1>
        <div style="margin-top:6px;font-size:18px;color:var(--muted)">I make web tools, analyzers and clean sites. <span class="typing-wrap"><span class="typing-text">Student Developer • Chart Analyzer • Web Designer • Python</span></span></div>
        <p class="bio">I build practical web projects like chart analysers for Indian, Forex and Crypto markets with ~83% approximate accuracy. Currently learning advanced web development while taking real projects for my portfolio.</p>
        <div class="cta">
          <a class="btn" href="#projects">See Projects</a>
          <a class="btn outline" href="#contact">Contact Me</a>
        </div>
      </div>

      <aside class="card">
        <div class="quick">
          <div class="stat"><div><strong>Location</strong><div class="small">Lucknow, India</div></div><div class="chip">Open to Remote</div></div>
          <div class="stat"><div><strong>Experience</strong><div class="small">Student Projects & College Event</div></div><div class="chip">Fresher</div></div>
          <div style="display:flex;gap:10px;align-items:center;justify-content:space-between">
            <div style="flex:1"><div style="font-weight:800">Crypto/Forex Analyzer</div><div class="small">~83% accuracy (event project)</div></div>
            <button class="btn" id="demoBtn">Live Demo</button>
          </div>
        </div>
      </aside>
    </main>

    <section id="skills">
      <h2 style="margin:0 0 12px 0">Skills</h2>
      <div class="grid-3">
        <div class="skill slide-up visible">
          <div class="name"><span>Java</span><span>75%</span></div>
          <div class="bar"><i style="width:75%"></i></div>
        </div>
        <div class="skill slide-up visible">
          <div class="name"><span>JavaScript</span><span>80%</span></div>
          <div class="bar"><i style="width:80%"></i></div>
        </div>
        <div class="skill slide-up visible">
          <div class="name"><span>HTML &amp; CSS</span><span>85%</span></div>
          <div class="bar"><i style="width:85%"></i></div>
        </div>
        <div class="skill slide-up visible">
          <div class="name"><span>Python</span><span>80%</span></div>
          <div class="bar"><i style="width:80%"></i></div>
        </div>
        <div class="skill slide-up visible">
          <div class="name"><span>Computer Science</span><span>83%</span></div>
          <div class="bar"><i style="width:83%"></i></div>
        </div>
        <div class="skill slide-up visible">
          <div class="name"><span>WordPress / Tools</span><span>72%</span></div>
          <div class="bar"><i style="width:72%"></i></div>
        </div>
      </div>
    </section>

    <section id="projects">
      <h2 style="margin:18px 0 12px 0">Projects</h2>
      <div class="grid-3">
        <div class="project" data-title="Chart Analyzer — Indian/Forex/Crypto" data-desc="A browser-based analyzer that reads market data and suggests entry & exit with ~83% accuracy. Built using Python for data logic and JS for visualization. Used in La Martiniere College event." data-more="Features: Live chart visualizations, entry/exit signals, accuracy tracking, CSV import/export, simple UI for traders.">
          <div class="proj-head"><strong>Chart Analyzer</strong><div class="chip">Event Project</div></div>
          <p style="color:var(--muted);margin-top:8px">Built for La Martiniere College event — provided clear entry/exit signals and visual chart analysis.</p>
        </div>

        <div class="project" data-title="Portfolio & Demo Pages" data-desc="Small landing pages and portfolio sites built using HTML/CSS and lightweight JS. Responsive + social-ready." data-more="Designed 1-page portfolio templates with sliding sections and pop animations.">
          <div class="proj-head"><strong>Portfolio Pages</strong><div class="chip">UI / Frontend</div></div>
          <p style="color:var(--muted);margin-top:8px">One-page websites and demos designed for creatives and students.</p>
        </div>

        <div class="project" data-title="Automation Scripts" data-desc="Python automation scripts for small tasks — scraping, CSV parsing, and simple data pipelines." data-more="Used for quick data extraction and preprocessing in event projects.">
          <div class="proj-head"><strong>Automation Scripts</strong><div class="chip">Python</div></div>
          <p style="color:var(--muted);margin-top:8px">Tools to speed up data handling and prototype ideas quickly.</p>
        </div>
      </div>
    </section>

    <section id="contact">
      <h2 style="margin:18px 0 12px 0">Contact</h2>
      <div class="card" style="display:flex;flex-direction:column;gap:12px">
        <div style="display:flex;justify-content:space-between;align-items:center">
          <div>
            <div style="font-weight:800">Email</div>
            <div class="small">ansh7224@outlook.com</div>
          </div>
          <div>
            <div style="font-weight:800">Phone</div>
            <div class="small">+91 9616757224</div>
          </div>
        </div>

        <div style="display:flex;gap:12px;flex-wrap:wrap">
          <a class="btn" href="mailto:ansh7224@outlook.com">Email Me</a>
          <a class="btn outline" href="tel:+919616757224">Call / WhatsApp</a>
        </div>

        <div style="margin-top:6px;color:var(--muted);font-size:14px">Or send a quick message:</div>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px">
          <input type="text" id="name" placeholder="Your name (or leave blank)" />
          <input type="text" id="subject" placeholder="Subject" />
        </div>
        <textarea id="message" rows="4" placeholder="Message"></textarea>
        <div style="display:flex;justify-content:flex-end">
          <button class="send" id="sendBtn">Send (opens email)</button>
        </div>
      </div>
    </section>

    <footer style="margin-top:28px;color:var(--muted);font-size:13px;text-align:center">Made with ❤ by Ansh Singh — Student Developer • La Martiniere College, Lucknow</footer>

  </div>

  <!-- Modal -->
  <div class="modal" id="modal">
    <div class="inner">
      <h3 id="mTitle">Project Title</h3>
      <div class="meta" id="mMeta">Event Project • La Martiniere College</div>
      <p id="mDesc">Full description goes here</p>
      <div style="display:flex;gap:10px;justify-content:flex-end;margin-top:12px">
        <a id="mDemo" class="btn" href="#" target="_blank">Open Demo</a>
        <button class="btn outline" id="mClose">Close</button>
      </div>
    </div>
  </div>

  <script>
    // Simple interactivity: modal popup for projects
    document.querySelectorAll('.project').forEach(node=>{
      node.addEventListener('click',()=>{
        const title=node.dataset.title;
        const desc=node.dataset.desc;
        const more=node.dataset.more;
        document.getElementById('mTitle').innerText=title;
        document.getElementById('mDesc').innerText=desc+"\n\n"+more;
        document.getElementById('mMeta').innerText='Event Project • La Martiniere College';
        document.getElementById('modal').classList.add('open');
      })
    })
    document.getElementById('mClose').addEventListener('click',()=>document.getElementById('modal').classList.remove('open'))
    document.getElementById('demoBtn').addEventListener('click',()=>{
      alert('Demo placeholder — you can link to a live demo or video here.');
    })

    // Send button opens mail client with prefilled message
    document.getElementById('sendBtn').addEventListener('click',()=>{
      const name=document.getElementById('name').value || 'No name';
      const subject=document.getElementById('subject').value || 'Portfolio message';
      const message=document.getElementById('message').value || '';
      const body = encodeURIComponent('From: '+name +'\n\n' + message + '\n\n-- Sent from portfolio site');
      window.location.href = 'mailto:ansh7224@outlook.com?subject='+encodeURIComponent(subject)+'&body='+body;
    })

    // reveal animations (simple)
    function reveal(){
      document.querySelectorAll('.slide-up').forEach(el => {
        const rect = el.getBoundingClientRect();
        if(rect.top < window.innerHeight - 60) el.classList.add('visible');
      })
    }
    window.addEventListener('scroll',reveal); window.addEventListener('load',reveal);

  </script>
</body>
</html>
