<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>GitHub Developer Dashboard</title>
  <style>
    :root {
      --bg-main: #1a1a1a;
      --bg-nav: #282828;
      --bg-card: #282828;
      --bg-subcard: #333333;
      --text-primary: #eff1f6;
      --text-secondary: #9ca3af;
      --accent-green: #2cbb5d;
      --accent-yellow: #ffc01e;
      --accent-red: #ef4743;
      --accent-blue: #3b82f6;
      --border-color: #3a3a3a;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background-color: var(--bg-main);
      color: var(--text-primary);
      min-height: 100vh;
    }

    /* Navbar */
    .navbar {
      background-color: var(--bg-nav);
      height: 52px;
      padding: 0 24px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 1px solid var(--border-color);
    }

    .nav-left {
      display: flex;
      align-items: center;
      gap: 24px;
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 8px;
      font-weight: 700;
      font-size: 18px;
      color: #fff;
    }

    .nav-links a {
      color: var(--text-secondary);
      text-decoration: none;
      font-size: 14px;
      margin-right: 18px;
      transition: color 0.2s;
    }

    .nav-links a:hover, .nav-links a.active {
      color: #fff;
    }

    .nav-right {
      display: flex;
      align-items: center;
      gap: 16px;
    }

    .search-box {
      background: #3a3a3a;
      border: none;
      border-radius: 6px;
      padding: 6px 12px;
      color: #fff;
      font-size: 13px;
      width: 200px;
    }

    .pro-badge {
      background: rgba(255, 192, 30, 0.15);
      color: var(--accent-yellow);
      padding: 4px 10px;
      border-radius: 6px;
      font-size: 12px;
      font-weight: 600;
    }

    /* Main Container */
    .container {
      max-width: 1220px;
      margin: 24px auto;
      padding: 0 16px;
      display: grid;
      grid-template-columns: 300px 1fr;
      gap: 20px;
    }

    /* Left Sidebar */
    .sidebar {
      background-color: var(--bg-card);
      border-radius: 10px;
      padding: 20px;
      height: fit-content;
    }

    .profile-header {
      display: flex;
      gap: 14px;
      align-items: center;
      margin-bottom: 16px;
    }

    .avatar {
      width: 72px;
      height: 72px;
      border-radius: 10px;
      background: linear-gradient(135deg, #3b82f6, #10b981);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 28px;
      font-weight: bold;
      color: #fff;
      object-fit: cover;
    }

    .profile-name h2 {
      font-size: 18px;
      font-weight: 600;
    }

    .profile-name p {
      font-size: 13px;
      color: var(--text-secondary);
      margin-top: 2px;
    }

    .rank-text {
      margin-top: 8px;
      font-size: 14px;
      color: var(--text-secondary);
    }

    .rank-text span {
      color: #fff;
      font-weight: 600;
    }

    .follow-stats {
      display: flex;
      gap: 16px;
      font-size: 13px;
      color: var(--text-secondary);
      margin: 14px 0;
    }

    .follow-stats strong {
      color: #fff;
    }

    .edit-btn {
      width: 100%;
      background-color: rgba(44, 187, 93, 0.15);
      color: var(--accent-green);
      border: none;
      padding: 9px;
      border-radius: 8px;
      font-weight: 600;
      font-size: 14px;
      cursor: pointer;
      transition: background 0.2s;
      margin-bottom: 18px;
    }

    .edit-btn:hover {
      background-color: rgba(44, 187, 93, 0.25);
    }

    .bio-list {
      list-style: none;
      border-bottom: 1px solid var(--border-color);
      padding-bottom: 16px;
      margin-bottom: 16px;
    }

    .bio-list li {
      font-size: 13px;
      color: var(--text-secondary);
      margin-bottom: 10px;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .section-title {
      font-size: 15px;
      font-weight: 600;
      margin-bottom: 14px;
    }

    .community-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 14px;
      font-size: 13px;
    }

    .community-item .label {
      color: var(--text-secondary);
    }

    .community-item .sub {
      font-size: 11px;
      color: #6b7280;
    }

    /* Right Dashboard Grid */
    .main-content {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }

    .row-2 {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }

    .card {
      background-color: var(--bg-card);
      border-radius: 10px;
      padding: 20px;
    }

    /* Top Stats & Graphs */
    .stat-header {
      display: flex;
      gap: 24px;
      margin-bottom: 12px;
    }

    .stat-block small {
      color: var(--text-secondary);
      font-size: 12px;
      display: block;
    }

    .stat-block strong {
      font-size: 22px;
      font-weight: 700;
    }

    .stat-block span {
      font-size: 14px;
      font-weight: 600;
    }

    /* Simple SVG Line Graph */
    .line-chart {
      width: 100%;
      height: 90px;
    }

    /* Bar Distribution Chart */
    .bar-chart {
      display: flex;
      align-items: flex-end;
      gap: 6px;
      height: 95px;
      padding-top: 15px;
    }

    .bar {
      flex: 1;
      background-color: #3e3e3e;
      border-radius: 3px 3px 0 0;
      transition: 0.3s;
    }

    .bar.highlight {
      background-color: var(--accent-yellow);
    }

    /* Middle Row: Ring & Badges */
    .solved-wrapper {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
    }

    .ring-container {
      position: relative;
      width: 130px;
      height: 130px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .ring-text {
      position: absolute;
      text-align: center;
    }

    .ring-text h3 {
      font-size: 22px;
    }

    .ring-text h3 span {
      font-size: 12px;
      color: var(--text-secondary);
    }

    .ring-text p {
      font-size: 12px;
      color: var(--accent-green);
    }

    .difficulty-list {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .diff-pill {
      background-color: var(--bg-subcard);
      padding: 8px 12px;
      border-radius: 8px;
      display: flex;
      justify-content: space-between;
      font-size: 13px;
    }

    .easy { color: #00b8a3; font-weight: 600; }
    .med { color: var(--accent-yellow); font-weight: 600; }
    .hard { color: var(--accent-red); font-weight: 600; }

    /* Badges */
    .badges-grid {
      display: flex;
      justify-content: space-around;
      margin: 18px 0;
    }

    .badge-hex {
      width: 64px;
      height: 64px;
      background: linear-gradient(145deg, #3a3a3a, #222);
      border: 2px solid #555;
      border-radius: 14px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-size: 11px;
      font-weight: bold;
      color: #fff;
      box-shadow: 0 4px 10px rgba(0,0,0,0.3);
    }

    /* Heatmap */
    .heatmap-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 14px;
      flex-wrap: wrap;
      gap: 10px;
    }

    .heatmap-grid {
      display: grid;
      grid-template-columns: repeat(52, 1fr);
      gap: 3px;
      overflow-x: auto;
    }

    .heat-col {
      display: flex;
      flex-direction: column;
      gap: 3px;
    }

    .heat-cell {
      width: 11px;
      height: 11px;
      border-radius: 2px;
      background-color: #333333;
    }

    .lvl-1 { background-color: #0e4429; }
    .lvl-2 { background-color: #006d32; }
    .lvl-3 { background-color: #26a641; }
    .lvl-4 { background-color: #39d353; }

    @media (max-width: 900px) {
      .container {
        grid-template-columns: 1fr;
      }
      .row-2 {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>

  <!-- Top Navigation -->
  <nav class="navbar">
    <div class="nav-left">
      <div class="logo">
        <svg height="24" width="24" viewBox="0 0 16 16" fill="white">
          <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/>
        </svg>
        GitDash
      </div>
      <div class="nav-links">
        <a href="#" class="active">Overview</a>
        <a href="#">Repositories</a>
        <a href="#">Projects</a>
        <a href="#">Packages</a>
        <a href="#">Stars</a>
      </div>
    </div>
    <div class="nav-right">
      <input type="text" class="search-box" placeholder="Search repos or code..." />
      <span class="pro-badge">PRO</span>
    </div>
  </nav>

  <!-- Main Layout -->
  <div class="container">
    
    <!-- Left Profile Sidebar -->
    <aside class="sidebar">
      <div class="profile-header">
        <div class="avatar">SK</div>
        <div class="profile-name">
          <h2>Shivam Kumar</h2>
          <p>@shivamkumar-dev</p>
          <div class="rank-text">Global Rank <span>124,592</span></div>
        </div>
      </div>

      <div class="follow-stats">
        <span><strong>42</strong> Following</span>
        <span><strong>128</strong> Followers</span>
      </div>

      <button class="edit-btn">Edit GitHub Profile</button>

      <ul class="bio-list">
        <li>📍 India</li>
        <li>🎓 Computer Science & AI</li>
        <li>🔗 github.com/shivamkumar-dev</li>
      </ul>

      <div class="section-title">Developer Stats</div>

      <div class="community-item">
        <div>
          <div class="label">👁️ Profile Views</div>
          <div class="sub">Last week +18</div>
        </div>
        <strong>1,420</strong>
      </div>

      <div class="community-item">
        <div>
          <div class="label">📦 Public Repos</div>
          <div class="sub">Last week +2</div>
        </div>
        <strong>34</strong>
      </div>

      <div class="community-item">
        <div>
          <div class="label">🔀 Pull Requests</div>
          <div class="sub">Merged</div>
        </div>
        <strong>19</strong>
      </div>

      <div class="community-item">
        <div>
          <div class="label">⭐ Total Stars</div>
          <div class="sub">Across repos</div>
        </div>
        <strong>86</strong>
      </div>
    </aside>

    <!-- Right Dashboard -->
    <main class="main-content">
      
      <!-- Row 1: Activity Rating & Top Percentile -->
      <div class="row-2">
        <div class="card">
          <div class="stat-header">
            <div class="stat-block">
              <small>Developer Score</small>
              <strong>1,642</strong>
            </div>
            <div class="stat-block">
              <small>Global Ranking</small>
              <span>124,592 / 900,000</span>
            </div>
            <div class="stat-block">
              <small>Repositories</small>
              <span>34</span>
            </div>
          </div>
          <!-- Line Chart -->
          <svg class="line-chart" viewBox="0 0 300 80">
            <polyline
              fill="none"
              stroke="#ffc01e"
              stroke-width="2.5"
              points="0,65 40,55 80,60 120,40 160,45 200,25 240,30 300,12"
            />
            <circle cx="300" cy="12" r="4" fill="#ffc01e" />
          </svg>
          <div style="display:flex; justify-content:space-between; font-size:11px; color:#9ca3af;">
            <span>Jan 2026</span>
            <span>Nov 2026</span>
          </div>
        </div>

        <div class="card">
          <div class="stat-block">
            <small>Top Contributor</small>
            <strong>14.87%</strong>
          </div>
          <div class="bar-chart">
            <div class="bar" style="height: 20%"></div>
            <div class="bar" style="height: 35%"></div>
            <div class="bar highlight" style="height: 85%"></div>
            <div class="bar" style="height: 65%"></div>
            <div class="bar" style="height: 50%"></div>
            <div class="bar" style="height: 40%"></div>
            <div class="bar" style="height: 28%"></div>
            <div class="bar" style="height: 18%"></div>
            <div class="bar" style="height: 12%"></div>
          </div>
        </div>
      </div>

      <!-- Row 2: Languages Ring & Badges -->
      <div class="row-2">
        <div class="card">
          <div class="solved-wrapper">
            <div class="ring-container">
              <svg width="130" height="130" viewBox="0 0 120 120">
                <circle cx="60" cy="60" r="50" stroke="#3a3a3a" stroke-width="8" fill="none" />
                <circle cx="60" cy="60" r="50" stroke="#2cbb5d" stroke-width="8" fill="none"
                  stroke-dasharray="314" stroke-dashoffset="75" stroke-linecap="round"
                  transform="rotate(-90 60 60)" />
              </svg>
              <div class="ring-text">
                <h3>501<span>/650</span></h3>
                <p>✓ Commits</p>
              </div>
            </div>

            <div class="difficulty-list">
              <div class="diff-pill">
                <span class="easy">Python / AI</span>
                <span>252 commits</span>
              </div>
              <div class="diff-pill">
                <span class="med">JavaScript</span>
                <span>186 commits</span>
              </div>
              <div class="diff-pill">
                <span class="hard">C++ / DSA</span>
                <span>63 commits</span>
              </div>
            </div>
          </div>
        </div>

        <div class="card">
          <div style="display:flex; justify-content:space-between;">
            <div>
              <small style="color:#9ca3af;">GitHub Badges</small>
              <h3 style="font-size:20px;">4</h3>
            </div>
            <span style="color:#9ca3af;">→</span>
          </div>

          <div class="badges-grid">
            <div class="badge-hex" style="border-color:#3b82f6;">🦈<br>Pull Shark</div>
            <div class="badge-hex" style="border-color:#a855f7;">🚀<br>YOLO</div>
            <div class="badge-hex" style="border-color:#2cbb5d;">❄️<br>Arctic</div>
          </div>

          <div>
            <small style="color:#9ca3af; font-size:11px;">Most Recent Badge</small>
            <div style="font-size:13px; font-weight:600;">200 Days Streak Badge 2026</div>
          </div>
        </div>
      </div>

      <!-- Row 3: Contribution Heatmap -->
      <div class="card">
        <div class="heatmap-header">
          <div>
            <strong style="font-size:16px;">1,075</strong>
            <span style="color:#9ca3af; font-size:14px;"> contributions in the past one year</span>
          </div>
          <div style="font-size:12px; color:#9ca3af;">
            Total active days: <strong style="color:#fff;">274</strong> &nbsp;|&nbsp; 
            Max streak: <strong style="color:#fff;">46</strong>
          </div>
        </div>

        <div class="heatmap-grid" id="heatmap"></div>
      </div>

    </main>
  </div>

  <script>
    // Generate realistic 52-week contribution heatmap
    const heatmap = document.getElementById("heatmap");
    const levels = ["", "lvl-1", "lvl-2", "lvl-3", "lvl-4"];

    for (let week = 0; week < 52; week++) {
      const col = document.createElement("div");
      col.className = "heat-col";
      for (let day = 0; day < 7; day++) {
        const cell = document.createElement("div");
        const rand = Math.random();
        let lvl = "";
        if (rand > 0.85) lvl = "lvl-4";
        else if (rand > 0.65) lvl = "lvl-3";
        else if (rand > 0.45) lvl = "lvl-2";
        else if (rand > 0.30) lvl = "lvl-1";

        cell.className = "heat-cell " + lvl;
        cell.title = `Week ${week + 1}, Day ${day + 1}`;
        col.appendChild(cell);
      }
      heatmap.appendChild(col);
    }
  </script>
</body>
</html>
