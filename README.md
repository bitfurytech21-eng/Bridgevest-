<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>BridgeVest Global — Building Wealth, Securing Futures</title>
  <!-- Google font -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">
  <!-- Chart.js CDN (for demo live charts) -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    :root{
      --blue-900:#032b5b;
      --blue-700:#0b4a8a;
      --blue-500:#1f73b7;
      --accent:#ffd166;
      --muted:#6b7280;
      --glass: rgba(255,255,255,0.06);
      --card: #ffffff;
      --radius:14px;
      font-family: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      color:#083042;
      background: linear-gradient(180deg,#eaf4ff 0%, #ffffff 100%);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      line-height:1.45;
    }
    /* Top language & auth bar */
    .topbar{
      display:flex;
      justify-content:space-between;
      gap:10px;
      padding:10px 20px;
      background:linear-gradient(90deg, rgba(255,255,255,0.25), rgba(255,255,255,0.12));
      align-items:center;
      border-bottom:1px solid rgba(10,20,30,0.04);
      position:sticky;
      top:0;
      z-index:40;
      backdrop-filter: blur(6px);
    }
    .lang-select{
      display:flex;
      gap:8px;
      align-items:center;
      font-size:14px;
      color:var(--blue-900);
    }
    .auth-actions{display:flex; gap:8px; align-items:center;}
    .btn{
      background:var(--blue-700);
      color:white;
      padding:8px 14px;
      border-radius:10px;
      border:0;
      cursor:pointer;
      font-weight:600;
      box-shadow: 0 6px 18px rgba(15,60,120,0.12);
    }
    .btn.ghost{background:transparent;color:var(--blue-700);border:1px solid rgba(15,60,120,0.08);box-shadow:none}
    .brand{display:flex;align-items:center;gap:12px;font-weight:700;color:var(--blue-900)}
    .brand .logo{
      width:44px;height:44px;border-radius:10px;background:linear-gradient(135deg,var(--blue-700),var(--blue-500));
      display:flex;align-items:center;justify-content:center;color:white;font-weight:800;
    }
    /* Hero */
    .hero{
      display:grid;
      grid-template-columns: 1fr 420px;
      gap:32px;
      align-items:center;
      padding:48px 6vw;
      min-height:68vh;
      background:
        linear-gradient(180deg, rgba(2,48,77,0.03), rgba(255,255,255,0.0));
    }
    .hero-left{
      max-width:820px;
    }
    .hero h1{
      font-size:34px;
      margin:0 0 12px 0;
      color:var(--blue-900);
      line-height:1.06;
    }
    .hero p{color:var(--muted);margin:0 0 18px 0; font-size:16px;}
    .hero .cta{display:flex;gap:12px}
    .hero-card{
      border-radius:18px;
      overflow:hidden;
      position:relative;
      box-shadow:0 24px 60px rgba(10,30,60,0.08);
      background:linear-gradient(180deg,rgba(255,255,255,0.6),rgba(255,255,255,0.4));
      padding:18px;
    }
    /* hero right image */
    .hero-visual{
      border-radius:16px;
      height:100%;
      min-height:280px;
      background-image: url("https://images.unsplash.com/photo-1509395176047-4a66953fd231?q=80&w=1400&auto=format&fit=crop&ixlib=rb-4.0.3&s=7f1f3c9c9cde785e2b2d0b7f3f5b5a0a");
      background-size:cover;
      background-position:center;
      position:relative;
      display:flex;
      flex-direction:column;
      justify-content:flex-end;
      color:white;
    }
    .hero-visual .overlay{
      padding:18px;
      background:linear-gradient(180deg, transparent, rgba(3,43,91,0.6));
    }
    /* sections */
    section{padding:36px 6vw}
    .container{max-width:1100px;margin:0 auto}
    .grid-3{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
    .card{
      background:white;
      border-radius:12px;
      padding:18px;
      box-shadow:0 12px 30px rgba(10,30,60,0.04);
    }
    .muted{color:var(--muted)}
    /* Live charts area */
    .charts {
      display:flex;
      gap:18px;
      align-items:stretch;
    }
    .chart-card{flex:1;padding:14px;border-radius:12px;background:linear-gradient(180deg,#ffffff,#f8fbff);}
    /* Programs & callouts */
    .programs{display:flex;gap:12px;flex-wrap:wrap}
    .program{flex:1;min-width:220px;padding:16px;border-radius:12px;background:linear-gradient(180deg,#fff,#f9fdff);}
    /* Footer */
    footer{
      padding:28px 6vw;
      background:linear-gradient(180deg, rgba(3,43,91,0.02), rgba(3,43,91,0.01));
      color:var(--muted);
    }
    .footer-grid{display:flex;gap:18px;flex-wrap:wrap;align-items:flex-start}
    /* modal */
    .modal-backdrop{position:fixed;inset:0;background:rgba(3,12,25,0.45);display:none;align-items:center;justify-content:center;z-index:80}
    .modal{background:white;border-radius:12px;padding:18px;min-width:320px;max-width:520px;box-shadow:0 30px 80px rgba(3,20,40,0.3)}
    .form-row{display:flex;flex-direction:column;gap:8px;margin-bottom:12px}
    input,select{padding:10px;border-radius:8px;border:1px solid rgba(10,20,30,0.06)}
    .small{font-size:13px;color:var(--muted)}
    /* responsive */
    @media (max-width:980px){
      .hero{grid-template-columns:1fr; padding:28px 4vw; gap:20px}
      .grid-3{grid-template-columns:1fr}
      .hero h1{font-size:28px}
      .topbar{padding:8px 12px}
      .hero-visual{min-height:220px}
    }
  </style>
</head>
<body>
  <!-- TOP BAR -->
  <div class="topbar">
    <div style="display:flex;align-items:center;gap:14px;">
      <div class="brand" aria-hidden="true">
        <div class="logo">BV</div>
        <div>
          <div style="font-size:14px">BridgeVest Global</div>
          <div class="small muted">Building Wealth, Securing Futures</div>
        </div>
      </div>
      <div class="lang-select">
        🌐
        <select aria-label="Select language" id="langSelect">
          <option>English</option>
          <option>French</option>
          <option>Spanish</option>
          <option>Chinese</option>
          <option>Arabic</option>
        </select>
      </div>
    </div>
    <div class="auth-actions">
      <button class="btn ghost" id="btnLogin">Login</button>
      <button class="btn" id="btnRegister">Create Account</button>
    </div>
  </div>
  <!-- HERO -->
  <header class="hero" role="banner">
    <div class="hero-left">
      <div style="display:flex;gap:10px;align-items:center;margin-bottom:8px">
        <div style="background:var(--accent);padding:6px 10px;border-radius:999px;font-weight:700;color:#07324a">New</div>
        <div class="small muted">Now open: Agriculture & Real Estate investments</div>
      </div>
      <h1>Your Bridge to Smarter Investments through Agriculture, Real Estate, and Beyond.</h1>
      <p>Where technology meets opportunity. Invest in verified agricultural and real estate ventures powered by transparency and innovation.</p>
      <div class="cta" style="margin-top:18px">
        <button class="btn" id="ctaLogin">Login</button>
        <button class="btn ghost" id="ctaCreate">Create Account</button>
      </div>
      <div style="margin-top:26px" class="hero-card">
        <strong>How it works</strong>
        <div style="display:flex;gap:10px;margin-top:12px;">
          <div style="flex:1">
            <div class="small muted">Step 1</div>
            <div>Register an account</div>
          </div>
          <div style="flex:1">
            <div class="small muted">Step 2</div>
            <div>Fund your account</div>
          </div>
          <div style="flex:1">
            <div class="small muted">Step 3</div>
            <div>Choose a plan & invest</div>
          </div>
        </div>
      </div>
    </div>
    <div class="hero-visual" aria-hidden="true">
      <div class="overlay">
        <div style="display:flex;justify-content:space-between;align-items:center;">
          <div>
            <div style="font-weight:700">BridgeVest Live</div>
            <div class="small">Agri & Property indices • Updated in real-time </div>
          </div>
          <div style="background:rgba(255,255,255,0.12);padding:8px;border-radius:10px;font-weight:600">Invest</div>
        </div>
      </div>
    </div>
  </header>
  <!-- ABOUT -->
  <section id="about">
    <div class="container">
      <div style="display:flex;justify-content:space-between;align-items:flex-start;gap:18px;flex-wrap:wrap">
        <div style="flex:1;min-width:300px">
          <h2>About BridgeVest Global</h2>
          <p class="muted">BridgeVest Global is a diversified asset management company transforming agriculture and real estate into transparent, high-yielding opportunities through a professional and technology-driven ecosystem. Our integrated model merges human expertise, AI forecasting, and blockchain transparency.</p>
          <p class="small muted"><strong>Vision:</strong> To make agriculture and real estate the world’s most accessible, trusted, and profitable investment classes.To democratize access to opportunities that drive food security, housing, and sustainable wealth globally. <br><strong>Mission:</strong> To bridge people from capital to opportunity, turning ordinary savings into growth through innovation, integrity, and expert management, connecting sustainable assets with smart financial technology.
Motto: “Building Wealth, Securing Futures.</p>
        </div>
        <div style="width:420px">
          <div class="card">
            <strong>Why choose BridgeVest</strong>
            <ul style="margin:10px 0 0 18px;color:var(--muted)">
              <li>Licensed & Certified — investor protection</li>
              <li>Blockchain-backed transparency</li>
              <li>Flexible Strategies across asset classes</li>
              <li>24/7 Live support</li>
            </ul>
            <div style="margin-top:12px;display:flex;gap:8px">
              <button class="btn" onclick="alert('Demo: Explore Plans')">Explore Our Plans</button>
              <button class="btn ghost" onclick="alert: Contact Support')">Contact</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
  <!-- INVESTMENTS -->
  <section id="investments" style="background:linear-gradient(180deg,rgba(15,70,130,0.02),transparent)">
    <div class="container">
      <h3>Our Best Investments</h3>
      <div class="grid-3" style="margin-top:14px">
        <div class="card">
          <h4>Agriculture Investment</h4>
          <p class="muted">Connect with real agricultural assets. Invest across value chains from plantations to processing.Here At BridgeVest, we connect investors with real agricultural assets through structured participation across global agricultural value chains.
Your investment serves as the seed managed by our professionals to yield measurable growth.Become a farmer today, without being on the farm.</p>
          <div style="display:flex;gap:8px;margin-top:10px">
            <button class="btn" onclick="alert('View Agricultural Plans (demo)')">View Plans</button>
            <button class="btn ghost" onclick="alert('Rent a Land (demo)')">Rent a land</button>
          </div>
        </div>
        <div class="card">
          <h4>Real Estate Investment</h4>
          <p class="muted">Property leasing, construction projects and estate development without hands on management.Join global real estate projects today with Bridgevest starting  from property leasing to construction and estate development without managing a single site yourself.</p>
          <div     style="display:flex;gap:8px;margin-top:10px">
           <button class="btn" onclick="alert('View Real Estate Plans)">View Plans</button>
            <button class="btn ghost" onclick="alert('Rent & Build')">Rent & Build</button>
          </div>
        </div>
        <div class="card">
  <!-- PROGRAMS -->
  <section id="programs">
    <div class="container">
      <h3>Programs & Initiatives</h3>
      <div class="programs" style="margin-top:12px">
        <div class="program">
          <strong>Investor Referral</strong>
          <div class="small muted">Earn commission for every successful referral.</div>
        </div>
        <div class="program">
          <strong>BridgeVest Partner</strong>
          <div class="small muted">Collaborate on verified projects worldwide.</div>
        </div>
        <div class="program">
          <strong>Learn & Earn</strong>
          <div class="small muted">Grow your investment knowledge while earning rewards.</div>
        </div>
      </div>
    </div>
  </section>
  <!-- Newsletter & Contact -->
  <section id="newsletter" style="background:linear-gradient(180deg,#f7fbff,#ffffff)">
    <div class="container" style="display:flex;gap:18px;align-items:center;justify-content:space-between;flex-wrap:wrap">
      <div style="flex:1;min-width:260px">
        <h3>Stay Ahead with BridgeVest Updates</h3>
        <p class="muted">Subscribe to receive project insights, forecasts and investor opportunities.</p>
      </div>
      <div style="min-width:320px;display:flex;gap:8px">
        <input id="newsletterEmail" placeholder="Enter Email Address" type="email" style="flex:1" />
        <button class="btn" onclick="subscribe()">Subscribe</button>
      </div>
    </div>
  </section>
  <!-- Contact & Social -->
  <section id="contact">
    <div class="container" style="display:flex;gap:18px;align-items:flex-start;flex-wrap:wrap">
      <div style="flex:1;min-width:300px">
        <h4>Contact Us</h4>
        <p class="muted">support@bridgevestglobal.com <br>WhatsApp: Direct Investor Line</p>
        <div class="small muted">Offices: Washington DC | London | Netherlands | California | Belgium</div>
      </div>
      <div style="min-width:220px">
        <h4>Social</h4>
        <div style="display:flex;flex-direction:column;gap:6px">
          <a href="#" class="small muted">Telegram – BridgeVest Global</a>
          <a href="#" class="small muted">Subscribe to Newsletter</a>
        </div>
      </div>
    </div>
  </section>
  <!-- FOOTER -->
  <footer>
    <div class="container">
      <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px">
        <div>© 2019 – 2025 BridgeVest Global. All Rights Reserved.</div>
        <div class="small muted">Licensed & Certified • Building Wealth, Securing Futures</div>
      </div>
    </div>
  </footer>
  <!-- Modal Backdrop for Login / Register -->
  <div class="modal-backdrop" id="modalBackdrop" role="dialog" aria-modal="true">
    <div class="modal" id="modalContent" role="document">
      <div id="modalInner">
        <!-- content injected by JS -->
      </div>
    </div>
  </div>
  <!-- Simple client-side JS to interactions and charts -->
  <script>
    // ---------- modal logic ----------
    const modalBackdrop = document.getElementById('modalBackdrop');
    const modalInner = document.getElementById('modalInner');
    function openModal(type = 'login') {
      if (type === 'login') {
        modalInner.innerHTML = `
          <h3 style="margin-top:0">Login</h3>
          <div class="form-row"><label class="small">Email</label><input id="loginEmail" type="email" /></div>
          <div class="form-row"><label class="small">Password</label><input id="loginPass" type="password" /></div>
          <div style="display:flex;gap:8px;justify-content:flex-end;">
            <button class="btn ghost" onclick="closeModal()">Cancel</button>
            <button class="btn" onclick="fakeLogin()">Sign in</button>
          </div>
        `;
      } else {
        modalInner.innerHTML = `
          <h3 style="margin-top:0">Create Account</h3>
          <div class="form-row"><label class="small">Full Name</label><input id="regName" type="text" /></div>
          <div class="form-row"><label class="small">Email</label><input id="regEmail" type="email" /></div>
          <div class="form-row"><label class="small">Password</label><input id="regPass" type="password" /></div>
          <div style="display:flex;gap:8px;justify-content:flex-end;">
            <button class="btn ghost" onclick="closeModal()">Cancel</button>
            <button class="btn" onclick="fakeRegister()">Create Account</button>
          </div>
        `;
      }
      modalBackdrop.style.display = 'flex';
    }
    function closeModal(){ modalBackdrop.style.display='none'; }    document.getElementById('btnLogin').addEventListener('click',()=>openModal('login')); document.getElementById('btnRegister').addEventListener('click',()=>openModal('register'))
document.getElementById('ctaLogin').addEventListener('click',()=>openModal('login'));
document.getElementById('ctaCreate').addEventListener('click',()=>openModal('register'));
    modalBackdrop.addEventListener('click',(e)=>{ if (e.target === modalBackdrop) closeModal(); });
    // ---------- auth / dashboard  ----------
    function Login(){
      // minimal simulation: close modal and show alert + dashboard header replacement
      closeModal();
      showDashboard();
    }
    function Register(){
      closeModal();
      alert('Account created . You are now logged in.');
      showDashboardMock();
    }
    function showDashboard(){
      // Replace topbar right area with investor snapshot
      const topbar = document.querySelector('.topbar .auth-actions');
      topbar.innerHTML = `
        <div style="display:flex;gap:10px;align-items:center;">
          <img src="https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?q=80&w=200&auto=format&fit=crop&ixlib=rb-4.0.3&s=9d9f3f7db1d1b7d9eb3a9c6b2f3b2a5c" style="width:36px;height:36px;border-radius:999px;object-fit:cover;border:2px solid white" alt="Investor"/>
          <div style="text-align:right">
            <div style="font-weight:700;font-size:14px">₿ 0.035</div>
            <div class="small muted">Account Balance</div>
          </div>
        </div>
        <button class="btn ghost" onclick="goToDashboard()">Dashboard</button><button class="btn" onclick="logout()">Logout</button>
      `
      alert('Welcome back — dashboard is available via the "Dashboard" button.');
    }
    function goToDashboard(){
      // quick scroll to top and reveal a small dashboard overlay card
window.scrollTo({top:0,behavior:'smooth'});
      const existing = document.getElementById('dashOverlay');
      if (existing) return existing.style.display = 'block';
      const overlay = document.createElement('div');
      overlay.id='dashOverlay';
      overlay.style.position='fixed';
      overlay.style.right='18px';
      overlay.style.top='80px';
      overlay.style.zIndex='90';
      overlay.style.minWidth='320px';
      overlay.style.borderRadius='12px';
      overlay.style.padding='14px';
      overlay.style.boxShadow='0 30px 70px rgba(3,20,40,0.2)';
      overlay.style.background='white';
      overlay.innerHTML = `
        <div style="display:flex;justify-content:space-between;align-items:center">
          <h4 style="margin:0">Investor Dashboard</h4>
          <button onclick="this.parentElement.parentElement.style.display='none'" class="btn ghost">Close</button>
        </div>
        <div style="margin-top:12px">
          <div class="small muted">Total Deposits</div>
          <div style="font-weight:700">₿ 0.120</div>
        </div>
        <div style="margin-top:8px">
          <div class="small muted">Total Investments</div>
          <div style="font-weight:700">₿ 0.085</div>
        </div>
        <div style="margin-top:12px;display:flex;gap:8px">
          <button class="btn" onclick="alert('Deposit flow (demo)')">Deposit</button>
          <button class="btn ghost" onclick="alert('Withdraw flow (demo)')">Withdraw</button>
        </div>
      `;
      document.body.appendChild(overlay);
    }
    function logout(){location.reload();
    }// ---------- newsletter ----------
    function subscribe(){
      const em = document.getElementById('newsletterEmail').value || '';
      if (!em.includes('@')) return alert('bitfurytech@protonmail.com');
      alert('Subscribed: ' + em .');
document.getElementById('newsletterEmail').value = '';
    }
    // ---------- charts with Chart.js ---------   // Commodity price demo (maize, cocoa, rice)
    const ctx1 = document.getElementById('commodityChart').getContext('2d');
    const commodityChart = new Chart(ctx1, {
      type:'line',
      data:{
        labels: ['Oct 28','Oct 29','Oct 30','Oct 31','Nov 1','Nov 2','Nov 3'],
        datasets:[
          {label:'Maize', data:[250,245,251,255,258,260,262], tension:0.3, fill:false, borderColor:'#1f73b7'},
          {label:'Cocoa', data:[1230,1245,1220,1210,1205,1235,1248], tension:0.3, fill:false, borderColor:'#0b4a8a'}
        ]
      },
      options:{
        responsive:true,
        plugins:{legend:{position:'bottom'}},
        scales:{
          y:{beginAtZero:false}
        }
      }
    });
    // Property index
    const ctx2 = document.getElementById('propertyChart').getContext('2d');
    const propertyChart = new Chart(ctx2, {
      type:'bar',
      data:{
        labels:['Q1','Q2','Q3','Q4'],
        datasets:[{label:'Urban Index Growth', data:[2.1,3.2,2.8
      },
      options:{
        responsive:true,
        plugins:{legend:{display:false}},
        scales:{y:{ticks:{callback: v => v + '%'}}}
      }
    });
    // small accessibility: lang select logs 
document.getElementById('langSelect').addEventListener('change', (e)=> {
      console.log('language selected:', e.target.value);
    });// keyboard: Enter opens login quick 
    window.addEventListener('keydown', (e)=>{ if (e.key==='/' && !e.metaKey) openModal('login'); });
  </script>
</body>
</html>
