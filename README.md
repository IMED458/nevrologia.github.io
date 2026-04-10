<html lang="ka">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>თრომბექტომია / ლიზისი — დოკუმენტები</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+Georgian:wght@300;400;500;600;700&display=swap');

/* ─── RESET ─── */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

/* ─── SCREEN VARIABLES ─── */
:root {
  --blue:   #1a4a7a;
  --blue2:  #2563a8;
  --line:   #1a4a7a;
  --bg:     #eef2f7;
  --card:   #ffffff;
  --border: #c8d4e3;
  --text:   #1e293b;
  --muted:  #64748b;
  --green:  #047857;
  --red:    #b91c1c;
  --amber:  #b45309;
}

body {
  font-family: 'Noto Sans Georgian', 'Sylfaen', Georgia, serif;
  background: var(--bg);
  color: var(--text);
  font-size: 14px;
  line-height: 1.65;
}

/* ══════════════════════════════════════════════
   TOC SCREEN
══════════════════════════════════════════════ */
#toc-screen {
  min-height: 100vh;
  display: flex; align-items: center; justify-content: center;
  padding: 24px;
}
.toc-card {
  background: white; border-radius: 16px;
  box-shadow: 0 8px 40px rgba(0,0,0,.15);
  padding: 40px 44px; max-width: 720px; width: 100%;
}
.toc-card h1 {
  font-size: 22px; color: var(--blue); font-weight: 700; margin-bottom: 4px;
}
.toc-card .sub { color: var(--muted); font-size: 13px; margin-bottom: 28px; }

.global-fields {
  display: flex; gap: 20px; flex-wrap: wrap;
  background: #f8fafc; border-radius: 10px;
  padding: 16px 20px; margin-bottom: 28px; border: 1px solid var(--border);
}
.gf-group { flex: 1; min-width: 200px; }
.gf-group label { display: block; font-size: 11px; color: var(--muted); margin-bottom: 5px; font-weight: 600; text-transform: uppercase; letter-spacing: .04em; }
.gf-group input {
  width: 100%; border: none; border-bottom: 2px solid var(--line);
  padding: 5px 0; font-size: 14px; font-family: inherit;
  background: transparent; outline: none; color: var(--text);
}
.gf-hint { font-size: 11px; color: var(--blue2); margin-top: 8px; font-style: italic; }

.doc-list { list-style: none; }
.doc-list li + li { border-top: 1px solid #f1f5f9; }
.doc-list a {
  display: flex; align-items: center; gap: 14px;
  padding: 14px 10px; text-decoration: none; color: var(--text);
  border-radius: 8px; transition: background .12s;
}
.doc-list a:hover { background: #f0f6ff; }
.doc-num {
  width: 32px; height: 32px; border-radius: 50%;
  background: var(--blue); color: white;
  display: flex; align-items: center; justify-content: center;
  font-size: 13px; font-weight: 700; flex-shrink: 0;
}
.doc-name { flex: 1; font-size: 14px; }
.doc-badge {
  font-size: 11px; background: #dbeafe; color: var(--blue);
  padding: 2px 9px; border-radius: 20px; flex-shrink: 0;
}

/* ══════════════════════════════════════════════
   DOCUMENT VIEWER
══════════════════════════════════════════════ */
#viewer { display: none; }

.top-bar {
  position: sticky; top: 0; z-index: 200;
  background: var(--blue); color: white;
  padding: 10px 20px; display: flex; align-items: center; gap: 14px;
  box-shadow: 0 2px 8px rgba(0,0,0,.25);
}
.top-bar h2 { flex: 1; font-size: 14px; font-weight: 600; }
.btn-back {
  background: rgba(255,255,255,.18); color: white; border: none;
  padding: 6px 15px; border-radius: 7px; cursor: pointer;
  font-family: inherit; font-size: 13px; transition: background .12s;
}
.btn-back:hover { background: rgba(255,255,255,.32); }
.btn-print {
  background: var(--green); color: white; border: none;
  padding: 7px 18px; border-radius: 7px; cursor: pointer;
  font-family: inherit; font-size: 13px; font-weight: 600;
  display: flex; align-items: center; gap: 6px; transition: background .12s;
}
.btn-print:hover { background: #065f46; }

/* Global info bar under topbar */
.info-bar {
  background: white; border-bottom: 2px solid var(--border);
  padding: 10px 24px; display: flex; gap: 24px; flex-wrap: wrap; align-items: center;
}
.info-bar .ib-group { display: flex; align-items: center; gap: 8px; }
.info-bar label { font-size: 11px; color: var(--muted); font-weight: 600; white-space: nowrap; }
.info-bar input {
  border: none; border-bottom: 2px solid var(--line);
  padding: 3px 0; font-size: 13px; font-family: inherit;
  min-width: 180px; background: transparent; outline: none; color: var(--text);
}
.ib-hint { margin-left: auto; font-size: 11px; color: var(--blue2); font-style: italic; }

/* Document page */
.doc-page {
  max-width: 820px; margin: 28px auto; padding: 0 20px 60px;
  display: none;
}
.doc-page.active { display: block; }

/* ══════════════════════════════════════════════
   DOCUMENT CONTENT STYLES (Word-like)
══════════════════════════════════════════════ */
.sheet {
  background: white;
  padding: 60px 64px;
  box-shadow: 0 2px 16px rgba(0,0,0,.10);
  border-radius: 4px;
  min-height: 297mm;
}

/* Typography */
.hd-row { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 6px; font-size: 13px; }
.hd-left { }
.hd-right { text-align: right; color: var(--muted); }

.doc-title {
  text-align: center; font-size: 16px; font-weight: 700;
  margin: 18px 0 22px; line-height: 1.5; color: var(--text);
}

/* Underline input — replaces "___" in original */
.ul {
  display: inline-block;
  border-bottom: 1.5px solid var(--line);
  min-width: 140px; padding: 1px 3px;
  font-family: inherit; font-size: 14px;
  background: transparent; outline: none;
  color: var(--text); vertical-align: bottom;
  transition: border-color .15s, background .15s;
}
.ul:focus { border-color: #0ea5e9; background: #f0f9ff; border-radius: 3px 3px 0 0; }
.ul.w-xs { min-width: 70px; }
.ul.w-sm { min-width: 110px; }
.ul.w-md { min-width: 180px; }
.ul.w-lg { min-width: 260px; }
.ul.w-xl { min-width: 340px; }
.ul.w-full { min-width: 100%; display: block; margin-top: 4px; }
input[type=date].ul, input[type=time].ul { min-width: 140px; }

/* Signature dash line */
.dash {
  display: inline-block; border-bottom: 1.5px dashed #94a3b8;
  min-width: 200px; vertical-align: bottom; margin: 0 4px;
}
.dash.lg { min-width: 280px; }
.dash.xl { min-width: 380px; }

/* Paragraph */
.p { margin: 10px 0; text-align: justify; }
.p.center { text-align: center; }
.bold { font-weight: 700; }

/* Numbered section */
.ns { margin: 12px 0 4px; font-weight: 700; }
.ns-body { margin: 0 0 10px 18px; text-align: justify; color: #334155; }

/* Horizontal rule */
.hr { border: none; border-top: 1px solid #e2e8f0; margin: 18px 0; }

/* Two column layout */
.cols2 { display: flex; gap: 40px; flex-wrap: wrap; margin: 14px 0; }
.cols2 > .col { flex: 1; min-width: 200px; }

/* Field row */
.fr { margin: 11px 0; }
.fr > label { display: block; font-size: 11px; color: var(--muted); margin-bottom: 4px; font-weight: 600; }

/* Warning block */
.warn {
  border: 1.5px solid #fca5a5; border-radius: 6px;
  padding: 14px 18px; margin: 16px 0; background: #fff7f7;
  font-size: 13px;
}

/* ── OQMI TABLE ── */
.oqmi-head { display: flex; flex-wrap: wrap; gap: 20px; margin-bottom: 16px; }
.oqmi-head .fr { min-width: 160px; }

.mon-table { width: 100%; border-collapse: collapse; font-size: 12.5px; margin: 10px 0; }
.mon-table th {
  background: var(--blue); color: white;
  padding: 7px 8px; border: 1px solid #c8d4e3;
  text-align: center; font-size: 12px;
}
.mon-table td {
  border: 1px solid #d1dae6; padding: 5px 7px;
  vertical-align: top; min-height: 44px;
}
.mon-table tr:nth-child(even) td { background: #f8fafc; }
.mon-table td input {
  border: none; border-bottom: 1px solid #94a3b8;
  width: 100%; font-family: inherit; font-size: 12px;
  background: transparent; outline: none; padding: 2px 0; margin-bottom: 3px;
}
.mon-table td textarea {
  border: 1px solid #cbd5e1; width: 100%;
  font-family: inherit; font-size: 12px; resize: vertical;
  min-height: 52px; padding: 4px; border-radius: 3px; outline: none;
}
.mon-table td textarea:focus, .mon-table td input:focus { border-color: #0ea5e9; }
.add-row-btn {
  background: var(--blue2); color: white; border: none;
  padding: 7px 16px; border-radius: 6px; cursor: pointer;
  font-family: inherit; font-size: 12px; margin-top: 8px;
}
.add-row-btn:hover { background: var(--blue); }

/* ── SCREENING TABLE ── */
.screen-section { margin: 16px 0; border: 1px solid var(--border); border-radius: 6px; overflow: hidden; }
.screen-sec-title {
  padding: 8px 14px; font-weight: 700; font-size: 13px; color: white;
}
.screen-sec-title.blue { background: var(--blue2); }
.screen-sec-title.red  { background: var(--red); }
.screen-sec-title.amber { background: var(--amber); }
.screen-item {
  display: flex; align-items: flex-start; justify-content: space-between;
  padding: 8px 14px; border-top: 1px solid #f1f5f9; gap: 20px;
}
.screen-item:first-child { border-top: none; }
.si-text { flex: 1; font-size: 13px; line-height: 1.5; }
.yn { display: flex; gap: 14px; flex-shrink: 0; padding-top: 1px; }
.yn label { display: flex; align-items: center; gap: 5px; font-size: 13px; cursor: pointer; }
.yn input[type=radio] { width: 15px; height: 15px; accent-color: var(--blue); cursor: pointer; }
.info-note {
  background: #f0f9ff; border-left: 3px solid #0ea5e9;
  padding: 8px 14px; border-radius: 0 5px 5px 0; font-size: 13px;
  color: #0369a1; margin: 12px 0;
}

/* ══════════════════════════════════════════════
   PRINT
══════════════════════════════════════════════ */
@media print {
  /* hide everything except active page */
  #toc-screen, .top-bar, .info-bar, .add-row-btn { display: none !important; }
  body { background: white !important; }
  #viewer { display: block !important; }
  .doc-page { display: none !important; max-width: none; margin: 0; padding: 0; }
  .doc-page.active { display: block !important; }
  .sheet {
    padding: 18mm 20mm !important;
    box-shadow: none !important; border-radius: 0 !important;
    min-height: unset !important;
  }
  /* no browser header/footer — user should set margins=none; we can't force it */
  @page { margin: 0; }

  /* keep colors */
  .screen-sec-title.blue  { background: var(--blue2) !important; -webkit-print-color-adjust: exact; print-color-adjust: exact; }
  .screen-sec-title.red   { background: var(--red)   !important; -webkit-print-color-adjust: exact; print-color-adjust: exact; }
  .screen-sec-title.amber { background: var(--amber) !important; -webkit-print-color-adjust: exact; print-color-adjust: exact; }
  .mon-table th { background: var(--blue) !important; -webkit-print-color-adjust: exact; print-color-adjust: exact; }
}
</style>
</head>
<body>

<!-- ══════════════════════════════════════════
     TOC SCREEN
══════════════════════════════════════════ -->
<div id="toc-screen">
  <div class="toc-card">
    <h1>🏥 თრომბექტომია / ლიზისი</h1>
    <p class="sub">სამედიცინო ფორმები — გახსენით სასურველი დოკუმენტი</p>

    <div class="global-fields">
      <div class="gf-group">
        <label>პაციენტის სახელი და გვარი</label>
        <input type="text" id="g-patient" placeholder="სახელი გვარი" oninput="propagate()">
      </div>
      <div class="gf-group">
        <label>ექიმის სახელი და გვარი</label>
        <input type="text" id="g-doctor" placeholder="სახელი გვარი" oninput="propagate()">
      </div>
      <p class="gf-hint" style="width:100%">✎ ერთხელ შეყვანილი მონაცემი ყველა ფორმაში ავტომატურად გადავა</p>
    </div>

    <ul class="doc-list">
      <li><a href="#" onclick="openDoc(0);return false;">
        <span class="doc-num">1</span>
        <span class="doc-name">პაციენტის წერილობითი თანხმობა — 36-ე დადგენილება (70%/30%)</span>
        <span class="doc-badge">ფორმა NIV</span>
      </a></li>
      <li><a href="#" onclick="openDoc(1);return false;">
        <span class="doc-num">2</span>
        <span class="doc-name">პაციენტის წერილობითი თანხმობა — 165-ე დადგენილება (90%/10%)</span>
        <span class="doc-badge">ფორმა NIV</span>
      </a></li>
      <li><a href="#" onclick="openDoc(2);return false;">
        <span class="doc-num">3</span>
        <span class="doc-name">პაციენტის წერილობითი თანხმობა — 218-ე დადგენილება (100%)</span>
        <span class="doc-badge">ფორმა NIV</span>
      </a></li>
      <li><a href="#" onclick="openDoc(3);return false;">
        <span class="doc-num">4</span>
        <span class="doc-name">პაციენტის წერილობითი თანხმობა — კერძო დაზღვევა</span>
        <span class="doc-badge">ფორმა NIV</span>
      </a></li>
      <li><a href="#" onclick="openDoc(4);return false;">
        <span class="doc-num">5</span>
        <span class="doc-name">სისტემური თრომბოლიზისის სკრინინგის კითხვარი</span>
        <span class="doc-badge">სკრინინგი</span>
      </a></li>
      <li><a href="#" onclick="openDoc(5);return false;">
        <span class="doc-num">6</span>
        <span class="doc-name">თრომბოლიზისის ოქმი — ვიტალური მონიტორინგი</span>
        <span class="doc-badge">ოქმი PHXX00</span>
      </a></li>
    </ul>
  </div>
</div>

<!-- ══════════════════════════════════════════
     VIEWER
══════════════════════════════════════════ -->
<div id="viewer">

  <!-- Top bar -->
  <div class="top-bar">
    <button class="btn-back" onclick="showTOC()">← სია</button>
    <h2 id="vbar-title"></h2>
    <button class="btn-print" onclick="doPrint()">🖨&nbsp; ბეჭდვა</button>
  </div>

  <!-- Info bar -->
  <div class="info-bar">
    <div class="ib-group">
      <label>პაციენტი:</label>
      <input type="text" id="b-patient" placeholder="სახელი გვარი" oninput="syncBar('patient')">
    </div>
    <div class="ib-group">
      <label>ექიმი:</label>
      <input type="text" id="b-doctor" placeholder="სახელი გვარი" oninput="syncBar('doctor')">
    </div>
    <span class="ib-hint">ცვლილება ყველა ფორმაში გადადის</span>
  </div>

  <!-- ─────────────────────────────────────────
       DOC 0 — 36-ე დადგ. (70/30)
  ───────────────────────────────────────── -->
  <div class="doc-page" id="doc-0">
  <div class="sheet">
    <div class="hd-row">
      <span class="bold">დანართი 13</span>
      <span>სამედიცინო დოკუმენტაცია ფორმა NIV</span>
    </div>

    <div class="doc-title">
      პაციენტის წერილობითი ინფორმაციული თანხმობა სამედიცინო<br>მომსახურეობის გაწევაზე
    </div>

    <div class="p">
      მე,&nbsp;&nbsp;<input type="text" class="ul w-lg patient-f" data-doc="0" placeholder="სახელი / გვარი / პირადი ნომერი" oninput="onPatient(this)">&nbsp;&nbsp;
      (პაციენტი,/ პაციენტის ოჯახის წევრი,/კანონიერი წარმომადგენელი (პირადი ნომერი)
    </div>
    <div class="p" style="padding-left:60px;">(სახელი/გვარი)</div>

    <div class="p">ექიმი-ნევროლოგისგან სრულად და ამომწურავად, მივიღე ინფორმაცია სამედიცინო მომსახურეობის გაწევის შესახებ, მათ შორის:</div>

    <div class="ns">1. სამედიცინო მომსახურეობის არსის და საჭიროების შესახებ:</div>
    <div class="ns-body">აღნიშნული დიაგნოზი – თავის ტვინის ინფარქტი განვითარებული ცერებრული არტერიების დაუზუსტებელი ოკლუზიისა ან სტენოზის გამო – მოითხოვს გადაუდებელ სტაციონარულ მკურნალობას, დამატებით კლინიკო-ლაბორატორიულ კვლვებს, გადაუდებელ რეკანალიზაციურ თერაპიას.</div>

    <div class="ns">2. სამედიცინო მომსახურეობის მოსალოდნელი შედეგების შესახებ:</div>
    <div class="ns-body">ინსულტის განვითარებამდე არსებული სტატუსის აღდგენა, ინვალიდიზაციის ხარისხის შემცირების ან/და ნევროლოგიური დეფიციტის სრულად/ნაწილობრივ აღდგენის ან სტაბილიზაციის მიზნით. ჰემოდინამიკის სტაბილიზირება, ვიტალური ფუნქციების სტაბილიზაცია.</div>

    <div class="ns">3. პაციენტის ჯანმრთელობის და სიცოცხლისათვის ამ მომსახურებასთან დაკავშირებული რისკის შესახებ:</div>
    <div class="ns-body">მედიკამენტოზური ალერგია, გასტრო-ინტესტინალური სისხლდენა, იშემიური ინსულტის განმეორება, სასიცოცხლო ფუნქციების მოშლა, ჰემორაგიული ინსულტი ან/და ლეტალური გამოსავალი. ინვაზიური პროცედურების ჩატარების დროს: შარდის ბუშტის კათეტერიზაცია — ჰემატურია, საშარდე გზების ინფექციის რისკის მომატება, პერიფერიული ვენური კათეტერი — ფლებიტი, ართერიული ხაზი — ჰემატომა.</div>

    <div class="ns">4. განზრახული სამედიცინო მომსახურებების, სხვა ალტერნატული ვარიანტებისა, მათი თანმხლები რისკისა და შესაძლო ეფექტების შესახებ:</div>
    <div class="ns-body">პაციენტი საჭიროებს ინსულტის მწვავე თერაპიას — თრომბოლიზისის/თრომბექტომიის ჩატარებას ინვალიდიზაციის ხარისხის შემცირების ან/და ნევროლოგიური დეფიციტის სრულად/ნაწილობრივ აღდგენის ან სტაბილიზაციის მიზნით. ინფორმირებული ვარ, რომ ზემოთ აღნიშნული თერაპიის ეფექტურობა დამოკიდებულია დროზე ინსულტის სიმპტომების დაწყებიდან.</div>

    <div class="ns">5. სამედიცინო მომსახურეობაზე უარის თქმის მოსალოდნელი შედეგების შესახებ:</div>
    <div class="ns-body">დაავადების პროგრესირება, რეინსულტი, სრული ინვალიდიზაცია, სასიცოცხლო ფუნქციების მოშლა, შესაძლო ლეტალური (სასიკვდილო) გამოსავალი.</div>

    <div class="ns">6. ფინანსური და სოციალური საკითხის შესახებ:</div>
    <div class="ns-body">დეტალურ ინფორმაციას მომაწვდის ნეიროქირურგიული განყოფილების ფინანსური მენეჯერი. სამედიცინო მომსახურეობის ხარჯების <strong>70%</strong> დაფარავს სოციალური მომსახურეობის სააგენტო, ხოლო <strong>30%</strong>-ს — პაციენტი/ პაციენტის ოჯახის წევრები.</div>

    <div class="hr"></div>

    <div class="p">პაციენტს / პაციენტის ოჯახის წევრებს, პასუხი გაეცა ყველა სხვა საინტერესო შეკითხვაზე და ხელის მოწერით ადასტურებს, რომ ზემოთ ხსენებულთან დაკავშირებით პრეტენზიები არ გააჩნია:</div>

    <div class="cols2" style="margin-top:18px;">
      <div class="col">
        <div class="fr"><label>ექიმი / ნევროლოგი</label><input type="text" class="ul w-md doctor-f" data-doc="0" placeholder="სახელი გვარი" oninput="onDoctor(this)"></div>
        <div class="fr" style="margin-top:14px;"><label>ხელმოწერა</label><span class="dash xl"></span></div>
        <div class="fr" style="margin-top:14px;"><label>თარიღი</label><input type="date" class="ul w-sm"></div>
      </div>
      <div class="col">
        <div class="fr"><label>პაციენტის ნათესავის / კანონიერი წარმომადგენლის სახელი გვარი</label><input type="text" class="ul w-lg"></div>
        <div class="fr" style="margin-top:14px;"><label>ხელმოწერა (თუ პაციენტი ვერ შემოდის კონტაქტში)</label><span class="dash xl"></span></div>
      </div>
    </div>

    <div class="hr"></div>
    <div class="warn">
      <strong>პაციენტი არ არის თანახმა შეთავაზებულ მკურნალობაზე</strong>, რასაც ადასტურებს საკუთარი ხელის მოწერით:<br><br>
      ხელმოწერა:&nbsp;<span class="dash lg"></span>&nbsp;&nbsp;&nbsp;სახელი/გვარი:&nbsp;<span class="dash lg"></span>
    </div>
  </div>
  </div><!-- /doc-0 -->


  <!-- ─────────────────────────────────────────
       DOC 1 — 165-ე დადგ. (90/10)
  ───────────────────────────────────────── -->
  <div class="doc-page" id="doc-1">
  <div class="sheet">
    <div class="hd-row">
      <span class="bold">დანართი 13</span>
      <span>სამედიცინო დოკუმენტაცია ფორმა NIV</span>
    </div>

    <div class="doc-title">
      პაციენტის წერილობითი ინფორმაციული თანხმობა სამედიცინო<br>მომსახურეობის გაწევაზე
    </div>

    <div class="p">
      მე,&nbsp;&nbsp;<input type="text" class="ul w-lg patient-f" data-doc="1" placeholder="სახელი / გვარი / პირადი ნომერი" oninput="onPatient(this)">&nbsp;&nbsp;
      (პაციენტი,/ პაციენტის ოჯახის წევრი,/კანონიერი წარმომადგენელი (პირადი ნომერი)
    </div>
    <div class="p" style="padding-left:60px;">(სახელი/გვარი)</div>

    <div class="p">ექიმი-ნევროლოგისგან სრულად და ამომწურავად, მივიღე ინფორმაცია სამედიცინო მომსახურეობის გაწევის შესახებ, მათ შორის:</div>

    <div class="ns">1. სამედიცინო მომსახურეობის არსის და საჭიროების შესახებ:</div>
    <div class="ns-body">აღნიშნული დიაგნოზი – თავის ტვინის ინფარქტი განვითარებული ცერებრული არტერიების დაუზუსტებელი ოკლუზიისა ან სტენოზის გამო – მოითხოვს გადაუდებელ სტაციონარულ მკურნალობას, დამატებით კლინიკო-ლაბორატორიულ კვლვებს, გადაუდებელ რეკანალიზაციურ თერაპიას.</div>

    <div class="ns">2. სამედიცინო მომსახურეობის მოსალოდნელი შედეგების შესახებ:</div>
    <div class="ns-body">ინსულტის განვითარებამდე არსებული სტატუსის აღდგენა, ინვალიდიზაციის ხარისხის შემცირების ან/და ნევროლოგიური დეფიციტის სრულად/ნაწილობრივ აღდგენის ან სტაბილიზაციის მიზნით. ჰემოდინამიკის სტაბილიზირება, ვიტალური ფუნქციების სტაბილიზაცია.</div>

    <div class="ns">3. პაციენტის ჯანმრთელობის და სიცოცხლისათვის ამ მომსახურებასთან დაკავშირებული რისკის შესახებ:</div>
    <div class="ns-body">მედიკამენტოზური ალერგია, გასტრო-ინტესტინალური სისხლდენა, იშემიური ინსულტის განმეორება, სასიცოცხლო ფუნქციების მოშლა, ჰემორაგიული ინსულტი ან/და ლეტალური გამოსავალი. ინვაზიური პროცედურების ჩატარების დროს: შარდის ბუშტის კათეტერიზაცია — ჰემატურია, საშარდე გზების ინფექციის რისკის მომატება, პერიფერიული ვენური კათეტერი — ფლებიტი, ართერიული ხაზი — ჰემატომა.</div>

    <div class="ns">4. განზრახული სამედიცინო მომსახურებების, სხვა ალტერნატული ვარიანტებისა, მათი თანმხლები რისკისა და შესაძლო ეფექტების შესახებ:</div>
    <div class="ns-body">პაციენტი საჭიროებს ინსულტის მწვავე თერაპიას — თრომბოლიზისის/თრომბექტომიის ჩატარებას. ინფორმირებული ვარ, რომ ზემოთ აღნიშნული თერაპიის ეფექტურობა დამოკიდებულია დროზე ინსულტის სიმპტომების დაწყებიდან.</div>

    <div class="ns">5. სამედიცინო მომსახურეობაზე უარის თქმის მოსალოდნელი შედეგების შესახებ:</div>
    <div class="ns-body">დაავადების პროგრესირება, რეინსულტი, სრული ინვალიდიზაცია, სასიცოცხლო ფუნქციების მოშლა, შესაძლო ლეტალური (სასიკვდილო) გამოსავალი.</div>

    <div class="ns">6. ფინანსური და სოციალური საკითხის შესახებ:</div>
    <div class="ns-body">დეტალურ ინფორმაციას მომაწვდის ნეიროქირურგიული განყოფილების ფინანსური მენეჯერი. სამედიცინო მომსახურეობის ხარჯების <strong>90%</strong> დაფარავს სოციალური მომსახურეობის სააგენტო, ხოლო <strong>10%</strong>-ს — პაციენტი/ პაციენტის ოჯახის წევრები.</div>

    <div class="hr"></div>

    <div class="p">პაციენტს / პაციენტის ოჯახის წევრებს, პასუხი გაეცა ყველა სხვა საინტერესო შეკითხვაზე და ხელის მოწერით ადასტურებს, რომ ზემოთ ხსენებულთან დაკავშირებით პრეტენზიები არ გააჩნია:</div>

    <div class="cols2" style="margin-top:18px;">
      <div class="col">
        <div class="fr"><label>ექიმი / ნევროლოგი</label><input type="text" class="ul w-md doctor-f" data-doc="1" placeholder="სახელი გვარი" oninput="onDoctor(this)"></div>
        <div class="fr" style="margin-top:14px;"><label>ხელმოწერა</label><span class="dash xl"></span></div>
        <div class="fr" style="margin-top:14px;"><label>თარიღი</label><input type="date" class="ul w-sm"></div>
      </div>
      <div class="col">
        <div class="fr"><label>პაციენტის ნათესავის / კანონიერი წარმომადგენლის სახელი გვარი</label><input type="text" class="ul w-lg"></div>
        <div class="fr" style="margin-top:14px;"><label>ხელმოწერა (თუ პაციენტი ვერ შემოდის კონტაქტში)</label><span class="dash xl"></span></div>
      </div>
    </div>

    <div class="hr"></div>
    <div class="warn">
      <strong>პაციენტი არ არის თანახმა შეთავაზებულ მკურნალობაზე</strong>, რასაც ადასტურებს საკუთარი ხელის მოწერით:<br><br>
      ხელმოწერა:&nbsp;<span class="dash lg"></span>&nbsp;&nbsp;&nbsp;სახელი/გვარი:&nbsp;<span class="dash lg"></span>
    </div>
  </div>
  </div><!-- /doc-1 -->


  <!-- ─────────────────────────────────────────
       DOC 2 — 218-ე დადგ. (100%)
  ───────────────────────────────────────── -->
  <div class="doc-page" id="doc-2">
  <div class="sheet">
    <div class="hd-row">
      <span class="bold">დანართი 13</span>
      <span>სამედიცინო დოკუმენტაცია ფორმა NIV</span>
    </div>

    <div class="doc-title">
      პაციენტის წერილობითი ინფორმაციული თანხმობა სამედიცინო<br>მომსახურეობის გაწევაზე
    </div>

    <div class="p">
      მე,&nbsp;&nbsp;<input type="text" class="ul w-lg patient-f" data-doc="2" placeholder="სახელი / გვარი / პირადი ნომერი" oninput="onPatient(this)">&nbsp;&nbsp;
      (პაციენტი,/ პაციენტის ოჯახის წევრი,/კანონიერი წარმომადგენელი (პირადი ნომერი)
    </div>
    <div class="p" style="padding-left:60px;">(სახელი/გვარი)</div>

    <div class="p">ექიმი-ნევროლოგისგან სრულად და ამომწურავად, მივიღე ინფორმაცია სამედიცინო მომსახურეობის გაწევის შესახებ, მათ შორის:</div>

    <div class="ns">1. სამედიცინო მომსახურეობის არსის და საჭიროების შესახებ:</div>
    <div class="ns-body">აღნიშნული დიაგნოზი – თავის ტვინის ინფარქტი განვითარებული ცერებრული არტერიების დაუზუსტებელი ოკლუზიისა ან სტენოზის გამო – მოითხოვს გადაუდებელ სტაციონარულ მკურნალობას, დამატებით კლინიკო-ლაბორატორიულ კვლვებს, გადაუდებელ რეკანალიზაციურ თერაპიას.</div>

    <div class="ns">2. სამედიცინო მომსახურეობის მოსალოდნელი შედეგების შესახებ:</div>
    <div class="ns-body">ინსულტის განვითარებამდე არსებული სტატუსის აღდგენა, ინვალიდიზაციის ხარისხის შემცირების ან/და ნევროლოგიური დეფიციტის სრულად/ნაწილობრივ აღდგენის ან სტაბილიზაციის მიზნით. ჰემოდინამიკის სტაბილიზირება, ვიტალური ფუნქციების სტაბილიზაცია.</div>

    <div class="ns">3. პაციენტის ჯანმრთელობის და სიცოცხლისათვის ამ მომსახურებასთან დაკავშირებული რისკის შესახებ:</div>
    <div class="ns-body">მედიკამენტოზური ალერგია, გასტრო-ინტესტინალური სისხლდენა, იშემიური ინსულტის განმეორება, სასიცოცხლო ფუნქციების მოშლა, ჰემორაგიული ინსულტი ან/და ლეტალური გამოსავალი. ინვაზიური პროცედურების ჩატარების დროს: შარდის ბუშტის კათეტერიზაცია — ჰემატურია, საშარდე გზების ინფექციის რისკის მომატება, პერიფერიული ვენური კათეტერი — ფლებიტი, ართერიული ხაზი — ჰემატომა.</div>

    <div class="ns">4. განზრახული სამედიცინო მომსახურებების, სხვა ალტერნატული ვარიანტებისა, მათი თანმხლები რისკისა და შესაძლო ეფექტების შესახებ:</div>
    <div class="ns-body">პაციენტი საჭიროებს ინსულტის მწვავე თერაპიას — თრომბოლიზისის/თრომბექტომიის ჩატარებას. ინფორმირებული ვარ, რომ ზემოთ აღნიშნული თერაპიის ეფექტურობა დამოკიდებულია დროზე ინსულტის სიმპტომების დაწყებიდან.</div>

    <div class="ns">5. სამედიცინო მომსახურეობაზე უარის თქმის მოსალოდნელი შედეგების შესახებ:</div>
    <div class="ns-body">დაავადების პროგრესირება, რეინსულტი, სრული ინვალიდიზაცია, სასიცოცხლო ფუნქციების მოშლა, შესაძლო ლეტალური (სასიკვდილო) გამოსავალი.</div>

    <div class="ns">6. ფინანსური და სოციალური საკითხის შესახებ:</div>
    <div class="ns-body">დეტალურ ინფორმაციას მომაწვდის ნეიროქირურგიული განყოფილების ფინანსური მენეჯერი. სამედიცინო მომსახურეობის ხარჯების <strong>100%</strong> დაფარავს სოციალური მომსახურეობის სააგენტო.</div>

    <div class="hr"></div>

    <div class="p">პაციენტს / პაციენტის ოჯახის წევრებს, პასუხი გაეცა ყველა სხვა საინტერესო შეკითხვაზე და ხელის მოწერით ადასტურებს, რომ ზემოთ ხსენებულთან დაკავშირებით პრეტენზიები არ გააჩნია:</div>

    <div class="cols2" style="margin-top:18px;">
      <div class="col">
        <div class="fr"><label>ექიმი / ნევროლოგი</label><input type="text" class="ul w-md doctor-f" data-doc="2" placeholder="სახელი გვარი" oninput="onDoctor(this)"></div>
        <div class="fr" style="margin-top:14px;"><label>ხელმოწერა</label><span class="dash xl"></span></div>
        <div class="fr" style="margin-top:14px;"><label>თარიღი</label><input type="date" class="ul w-sm"></div>
      </div>
      <div class="col">
        <div class="fr"><label>პაციენტის ნათესავის / კანონიერი წარმომადგენლის სახელი გვარი</label><input type="text" class="ul w-lg"></div>
        <div class="fr" style="margin-top:14px;"><label>ხელმოწერა (თუ პაციენტი ვერ შემოდის კონტაქტში)</label><span class="dash xl"></span></div>
      </div>
    </div>

    <div class="hr"></div>
    <div class="warn">
      <strong>პაციენტი არ არის თანახმა შეთავაზებულ მკურნალობაზე</strong>, რასაც ადასტურებს საკუთარი ხელის მოწერით:<br><br>
      ხელმოწერა:&nbsp;<span class="dash lg"></span>&nbsp;&nbsp;&nbsp;სახელი/გვარი:&nbsp;<span class="dash lg"></span>
    </div>
  </div>
  </div><!-- /doc-2 -->


  <!-- ─────────────────────────────────────────
       DOC 3 — კერძო დაზღვევა
  ───────────────────────────────────────── -->
  <div class="doc-page" id="doc-3">
  <div class="sheet">
    <div class="hd-row">
      <span class="bold">დანართი 13</span>
      <span>სამედიცინო დოკუმენტაცია ფორმა NIV</span>
    </div>

    <div class="doc-title">
      პაციენტის წერილობითი ინფორმაციული თანხმობა სამედიცინო<br>მომსახურეობის გაწევაზე
    </div>

    <div class="p">
      მე,&nbsp;&nbsp;<input type="text" class="ul w-lg patient-f" data-doc="3" placeholder="სახელი / გვარი / პირადი ნომერი" oninput="onPatient(this)">&nbsp;&nbsp;
      (პაციენტი,/ პაციენტის ოჯახის წევრი,/კანონიერი წარმომადგენელი (პირადი ნომერი)
    </div>
    <div class="p" style="padding-left:60px;">(სახელი/გვარი)</div>

    <div class="p">ექიმი-ნევროლოგისგან სრულად და ამომწურავად, მივიღე ინფორმაცია სამედიცინო მომსახურეობის გაწევის შესახებ, მათ შორის:</div>

    <div class="ns">1. სამედიცინო მომსახურეობის არსის და საჭიროების შესახებ:</div>
    <div class="ns-body">აღნიშნული დიაგნოზი – თავის ტვინის ინფარქტი განვითარებული ცერებრული არტერიების დაუზუსტებელი ოკლუზიისა ან სტენოზის გამო – მოითხოვს გადაუდებელ სტაციონარულ მკურნალობას, დამატებით კლინიკო-ლაბორატორიულ კვლვებს, გადაუდებელ რეკანალიზაციურ თერაპიას.</div>

    <div class="ns">2. სამედიცინო მომსახურეობის მოსალოდნელი შედეგების შესახებ:</div>
    <div class="ns-body">ინსულტის განვითარებამდე არსებული სტატუსის აღდგენა, ინვალიდიზაციის ხარისხის შემცირების ან/და ნევროლოგიური დეფიციტის სრულად/ნაწილობრივ აღდგენის ან სტაბილიზაციის მიზნით. ჰემოდინამიკის სტაბილიზირება, ვიტალური ფუნქციების სტაბილიზაცია.</div>

    <div class="ns">3. პაციენტის ჯანმრთელობის და სიცოცხლისათვის ამ მომსახურებასთან დაკავშირებული რისკის შესახებ:</div>
    <div class="ns-body">მედიკამენტოზური ალერგია, გასტრო-ინტესტინალური სისხლდენა, იშემიური ინსულტის განმეორება, სასიცოცხლო ფუნქციების მოშლა, ჰემორაგიული ინსულტი ან/და ლეტალური გამოსავალი. ინვაზიური პროცედურების ჩატარების დროს: შარდის ბუშტის კათეტერიზაცია — ჰემატურია, საშარდე გზების ინფექციის რისკის მომატება, პერიფერიული ვენური კათეტერი — ფლებიტი, ართერიული ხაზი — ჰემატომა.</div>

    <div class="ns">4. განზრახული სამედიცინო მომსახურებების, სხვა ალტერნატული ვარიანტებისა, მათი თანმხლები რისკისა და შესაძლო ეფექტების შესახებ:</div>
    <div class="ns-body">პაციენტი საჭიროებს ინსულტის მწვავე თერაპიას — თრომბოლიზისის/თრომბექტომიის ჩატარებას. ინფორმირებული ვარ, რომ ზემოთ აღნიშნული თერაპიის ეფექტურობა დამოკიდებულია დროზე ინსულტის სიმპტომების დაწყებიდან.</div>

    <div class="ns">5. სამედიცინო მომსახურეობაზე უარის თქმის მოსალოდნელი შედეგების შესახებ:</div>
    <div class="ns-body">დაავადების პროგრესირება, რეინსულტი, სრული ინვალიდიზაცია, სასიცოცხლო ფუნქციების მოშლა, შესაძლო ლეტალური (სასიკვდილო) გამოსავალი.</div>

    <div class="ns">6. ფინანსური და სოციალური საკითხის შესახებ:</div>
    <div class="ns-body">დეტალურ ინფორმაციას მომაწვდის ნეიროქირურგიული განყოფილების ფინანსური მენეჯერი. სამედიცინო მომსახურეობის ხარჯებს სრულად ან ნაწილობრივ დაფარავს კერძო დაზღვევა ან პაციენტი/პაციენტის ოჯახის წევრი (სადაზღვევო კომპანიის მიერ დაუფინანსებელ ნაწილს).</div>

    <div class="hr"></div>

    <div class="p">პაციენტს / პაციენტის ოჯახის წევრებს, პასუხი გაეცა ყველა სხვა საინტერესო შეკითხვაზე და ხელის მოწერით ადასტურებს, რომ ზემოთ ხსენებულთან დაკავშირებით პრეტენზიები არ გააჩნია:</div>

    <div class="cols2" style="margin-top:18px;">
      <div class="col">
        <div class="fr"><label>ექიმი / ნევროლოგი</label><input type="text" class="ul w-md doctor-f" data-doc="3" placeholder="სახელი გვარი" oninput="onDoctor(this)"></div>
        <div class="fr" style="margin-top:14px;"><label>ხელმოწერა</label><span class="dash xl"></span></div>
        <div class="fr" style="margin-top:14px;"><label>თარიღი</label><input type="date" class="ul w-sm"></div>
      </div>
      <div class="col">
        <div class="fr"><label>პაციენტის ნათესავის / კანონიერი წარმომადგენლის სახელი გვარი</label><input type="text" class="ul w-lg"></div>
        <div class="fr" style="margin-top:14px;"><label>ხელმოწერა (თუ პაციენტი ვერ შემოდის კონტაქტში)</label><span class="dash xl"></span></div>
      </div>
    </div>

    <div class="hr"></div>
    <div class="warn">
      <strong>პაციენტი არ არის თანახმა შეთავაზებულ მკურნალობაზე</strong>, რასაც ადასტურებს საკუთარი ხელის მოწერით:<br><br>
      ხელმოწერა:&nbsp;<span class="dash lg"></span>&nbsp;&nbsp;&nbsp;სახელი/გვარი:&nbsp;<span class="dash lg"></span>
    </div>
  </div>
  </div><!-- /doc-3 -->


  <!-- ─────────────────────────────────────────
       DOC 4 — სკრინინგი
  ───────────────────────────────────────── -->
  <div class="doc-page" id="doc-4">
  <div class="sheet">
    <div class="doc-title" style="margin-top:0;">
      სისტემური თრომბოლიზი<br>სკრინინგი
    </div>

    <div class="cols2">
      <div class="col">
        <div class="fr"><label>პაციენტის სახელი, გვარი, ასაკი</label><input type="text" class="ul w-xl patient-f" data-doc="4" placeholder="სახელი გვარი, ასაკი" oninput="onPatient(this)"></div>
        <div class="fr" style="margin-top:10px;"><label>პაციენტის წონა (კგ)</label><input type="text" class="ul w-xs" placeholder="კგ"></div>
        <div class="fr" style="margin-top:10px;"><label>კლინიკაში მოყვანილია</label><input type="text" class="ul w-sm" placeholder="___"></div>
      </div>
      <div class="col">
        <div class="fr"><label>სკრინინგის დაწყების დრო</label><input type="time" class="ul w-sm"></div>
        <div class="fr" style="margin-top:10px;"><label>ინსულტის სიმპტომების დაწყების დრო</label><input type="datetime-local" class="ul"></div>
      </div>
    </div>

    <!-- INCLUSION -->
    <div class="screen-section" style="margin-top:18px;">
      <div class="screen-sec-title blue">ჩართვის კრიტერიუმები</div>

      <div class="screen-item"><span class="si-text">ინსულტის სიმპტომების დაწყების დრო &lt;4,5 სთ</span><div class="yn"><label><input type="radio" name="s_i1" value="y"> დიახ</label><label><input type="radio" name="s_i1" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">ასაკი &gt;18 წ</span><div class="yn"><label><input type="radio" name="s_i2" value="y"> დიახ</label><label><input type="radio" name="s_i2" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">პაციენტი არ არის კომაში</span><div class="yn"><label><input type="radio" name="s_i3" value="y"> დიახ</label><label><input type="radio" name="s_i3" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">NIHSS &lt;20 ქულა</span><div class="yn"><label><input type="radio" name="s_i4" value="y"> დიახ</label><label><input type="radio" name="s_i4" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">TA სისტოლური &lt;180, დიასტოლური &lt;110 მმ ვწ</span><div class="yn"><label><input type="radio" name="s_i5" value="y"> დიახ</label><label><input type="radio" name="s_i5" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">CT კვლევით გამოირიცხა ინტრაცერებრული სისხლჩაქცევა</span><div class="yn"><label><input type="radio" name="s_i6" value="y"> დიახ</label><label><input type="radio" name="s_i6" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">CT კვლევით არ ვლინდება ინფარქტის კერა ASPECTS (მეტი 7-ზე)</span><div class="yn"><label><input type="radio" name="s_i7" value="y"> დიახ</label><label><input type="radio" name="s_i7" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">გლიკემია: &gt;50 მგ% და &lt;400 მგ%</span><div class="yn"><label><input type="radio" name="s_i8" value="y"> დიახ</label><label><input type="radio" name="s_i8" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">ტემპერატურა: &lt;37.5°C</span><div class="yn"><label><input type="radio" name="s_i9" value="y"> დიახ</label><label><input type="radio" name="s_i9" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">APTT ნორმის ფარგლებშია</span><div class="yn"><label><input type="radio" name="s_i10" value="y"> დიახ</label><label><input type="radio" name="s_i10" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">INR &lt;1.2 (ლაბ. ნორმის ზედა ზღვარის ქვემოთ)</span><div class="yn"><label><input type="radio" name="s_i11" value="y"> დიახ</label><label><input type="radio" name="s_i11" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">თრომბოციტები &gt;100 000</span><div class="yn"><label><input type="radio" name="s_i12" value="y"> დიახ</label><label><input type="radio" name="s_i12" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">LMWH ჰეპარინის თერაპიული დოზა ბოლო 24სთ-ში — არ მიუღია</span><div class="yn"><label><input type="radio" name="s_i13" value="y"> დიახ</label><label><input type="radio" name="s_i13" value="n"> არა</label></div></div>
    </div>
    <div class="info-note">თუ ყველა პასუხი დადებითია — გააგრძელეთ კითხვარის შევსება.</div>

    <!-- ABSOLUTE CI -->
    <div class="screen-section">
      <div class="screen-sec-title red">აბსოლიტური უკუჩვენება</div>
      <div class="screen-item"><span class="si-text">გლიკემია ამ მომენტისთვის: &lt;50 ან &gt;400 მგ%</span><div class="yn"><label><input type="radio" name="s_a1" value="y"> დიახ</label><label><input type="radio" name="s_a1" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">პაციენტი კომაშია</span><div class="yn"><label><input type="radio" name="s_a2" value="y"> დიახ</label><label><input type="radio" name="s_a2" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">გადატანილი ინტრაკრანიალური სისხლჩაქცევა</span><div class="yn"><label><input type="radio" name="s_a3" value="y"> დიახ</label><label><input type="radio" name="s_a3" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">ბაქტერიული ენდოკარდიტი, პერიკარდიტი, მენინგიტი</span><div class="yn"><label><input type="radio" name="s_a4" value="y"> დიახ</label><label><input type="radio" name="s_a4" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">ქირურგიული ჩარევა ბოლო 3 თვის ვადაში</span><div class="yn"><label><input type="radio" name="s_a5" value="y"> დიახ</label><label><input type="radio" name="s_a5" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">უროგენიტალური / გასტროინტესტინალური სისხლდენა</span><div class="yn"><label><input type="radio" name="s_a6" value="y"> დიახ</label><label><input type="radio" name="s_a6" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">მძიმე ქალა-ტვინის ტრავმა ბოლო 3 თვის ვადაში</span><div class="yn"><label><input type="radio" name="s_a7" value="y"> დიახ</label><label><input type="radio" name="s_a7" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">ბოლო 7 დღის განმავლობაში ლუმბალური / არტერიის პუნქცია</span><div class="yn"><label><input type="radio" name="s_a8" value="y"> დიახ</label><label><input type="radio" name="s_a8" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">ბოლო 1 თვის განმავლობაში ნებისმიერი ხარისხის ტრავმა</span><div class="yn"><label><input type="radio" name="s_a9" value="y"> დიახ</label><label><input type="radio" name="s_a9" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">CT კვლევით — დიდი ზომის დაზიანება (MCA territory &gt;1/3)</span><div class="yn"><label><input type="radio" name="s_a10" value="y"> დიახ</label><label><input type="radio" name="s_a10" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">ორსულობა / მშობიარობა ბოლო 10 დღეში</span><div class="yn"><label><input type="radio" name="s_a11" value="y"> დიახ</label><label><input type="radio" name="s_a11" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">ბოლო 24 საათში: LMWH, vit K ანტაგონისტი (ვარფარინი)</span><div class="yn"><label><input type="radio" name="s_a12" value="y"> დიახ</label><label><input type="radio" name="s_a12" value="n"> არა</label></div></div>
    </div>

    <!-- RELATIVE CI -->
    <div class="screen-section">
      <div class="screen-sec-title amber">შედარებითი უკუჩვენება</div>
      <div class="screen-item"><span class="si-text">ასაკი 80+, სიმპტომების დაწყების დრო &gt;3 სთ</span><div class="yn"><label><input type="radio" name="s_r1" value="y"> დიახ</label><label><input type="radio" name="s_r1" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">ბოლო 3 თვის განმავლობაში გადატანილი იშემიური ინსულტი</span><div class="yn"><label><input type="radio" name="s_r2" value="y"> დიახ</label><label><input type="radio" name="s_r2" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">ინსულტის დასაწყისი უცნობია (Wake-up stroke)</span><div class="yn"><label><input type="radio" name="s_r3" value="y"> დიახ</label><label><input type="radio" name="s_r3" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">მსუბუქი სიმპტომატიკა, რომელიც სწრაფად გაუმჯობესდა</span><div class="yn"><label><input type="radio" name="s_r4" value="y"> დიახ</label><label><input type="radio" name="s_r4" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">პაციენტს აღენიშნა გულყრა / კრუნჩხვა სიმპტომების დაწყებისას</span><div class="yn"><label><input type="radio" name="s_r5" value="y"> დიახ</label><label><input type="radio" name="s_r5" value="n"> არა</label></div></div>
      <div class="screen-item"><span class="si-text">პაციენტს მიღებული აქვს ბოლო 48 საათში DOAC, NOAC</span><div class="yn"><label><input type="radio" name="s_r6" value="y"> დიახ</label><label><input type="radio" name="s_r6" value="n"> არა</label></div></div>
    </div>
    <div class="info-note">თუ ყველა აბსოლიტური უკუჩვენება უარყოფითია — პაციენტს შეიძლება ჩაუტარდეს სისტემური ი/ვ თრომბოლიზური თერაპია. შედარებითი უკუჩვენების დროს ინდივიდუალურად შეფასდება თრომბოლიზისის რისკი და სარგებელი.</div>

    <div class="hr"></div>

    <div class="cols2">
      <div class="col">
        <div class="fr"><label>პაციენტის / ოჯახის წევრის ინფ. თანხმობაზე ხელმოწერა</label>
          <div style="display:flex;gap:16px;margin-top:6px;">
            <label style="display:flex;align-items:center;gap:5px;cursor:pointer;"><input type="radio" name="s_consent"> დიახ</label>
            <label style="display:flex;align-items:center;gap:5px;cursor:pointer;"><input type="radio" name="s_consent"> არა</label>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="fr"><label>ნევროლოგის თანხმობა</label>
          <div style="display:flex;gap:16px;margin-top:6px;">
            <label style="display:flex;align-items:center;gap:5px;cursor:pointer;"><input type="radio" name="s_neuro"> დიახ</label>
            <label style="display:flex;align-items:center;gap:5px;cursor:pointer;"><input type="radio" name="s_neuro"> არა</label>
          </div>
        </div>
      </div>
    </div>

    <div class="cols2" style="margin-top:12px;">
      <div class="col">
        <div class="fr"><label>ალტეპლაზის (rTPA) ი/ვ დოზა (0.9 მგ/კგ, არაუმეტეს 90 მგ)</label><input type="text" class="ul w-sm" placeholder="მლ"></div>
        <div style="display:flex;gap:20px;margin-top:10px;">
          <div class="fr"><label>ბოლუსით</label><input type="text" class="ul w-xs" placeholder="მლ"></div>
          <div class="fr"><label>ინფუზით</label><input type="text" class="ul w-xs" placeholder="მლ/სთ"></div>
        </div>
      </div>
      <div class="col">
        <div class="fr"><label>თრომბოლიზის დაწყების დრო</label><input type="time" class="ul w-sm"></div>
        <div class="fr" style="margin-top:10px;"><label>ნევროლოგი</label><input type="text" class="ul w-md doctor-f" data-doc="4" placeholder="სახელი გვარი" oninput="onDoctor(this)"></div>
      </div>
    </div>
  </div>
  </div><!-- /doc-4 -->


  <!-- ─────────────────────────────────────────
       DOC 5 — ოქმი
  ───────────────────────────────────────── -->
  <div class="doc-page" id="doc-5">
  <div class="sheet">
    <div class="doc-title" style="font-size:15px;">
      ცენტრალური ვენური კათეტერის ან ვასკულარული საინექციო მიდგომის თრომბოლიზისი PHXX00
    </div>

    <div class="p center">ოქმი N&nbsp;<input type="text" class="ul w-xs" placeholder="____"></div>

    <div class="cols2" style="margin-top:14px;">
      <div class="col">
        <div class="fr"><label>პაციენტის სახელი და გვარი</label><input type="text" class="ul w-xl patient-f" data-doc="5" placeholder="სახელი გვარი" oninput="onPatient(this)"></div>
        <div class="fr" style="margin-top:10px;"><label>დაბადების თარიღი</label><input type="date" class="ul"></div>
        <div class="fr" style="margin-top:10px;"><label>ბარათის ნომერი</label><input type="text" class="ul w-sm" placeholder="XXXXX/XX"></div>
      </div>
      <div class="col">
        <div class="fr"><label>პაციენტის წონა (კგ)</label><input type="text" class="ul w-xs" placeholder="კგ"></div>
        <div class="fr" style="margin-top:10px;"><label>ალტეპლაზის (rTPA) ი/ვ დოზა (მლ)</label><input type="text" class="ul w-xs" placeholder="მლ"></div>
        <div style="display:flex;gap:16px;margin-top:10px;flex-wrap:wrap;">
          <div class="fr"><label>ბოლუსით (მლ)</label><input type="text" class="ul w-xs" placeholder="მლ"></div>
          <div class="fr"><label>ინფუზით (მლ/სთ)</label><input type="text" class="ul w-xs" placeholder="მლ/სთ"></div>
        </div>
      </div>
    </div>

    <div class="hr"></div>

    <div style="overflow-x:auto;">
      <table class="mon-table" id="mon-tbl">
        <thead>
          <tr>
            <th style="width:32%;">დრო / ნევროლ. სტატუსი (GCS, NIHSS)</th>
            <th style="width:14%;">გლიკემია (მგ/დლ)</th>
            <th style="width:26%;">სასიცოცხლო მაჩვ.<br><small>TA / HR / SpO2 / RR / T</small></th>
            <th style="width:28%;">მედიკამენტი / შენიშვნა</th>
          </tr>
        </thead>
        <tbody id="mon-body">
          <!-- rows built by JS -->
        </tbody>
      </table>
    </div>
    <button class="add-row-btn" onclick="addMonRow()">+ სტრიქონის დამატება</button>

    <div class="hr" style="margin-top:14px;"></div>

    <div class="cols2">
      <div class="col">
        <div class="fr"><label>ჩარევის თარიღი</label><input type="date" class="ul"></div>
        <div class="fr" style="margin-top:10px;"><label>დაწყების დრო</label><input type="time" class="ul w-sm"></div>
        <div class="fr" style="margin-top:10px;"><label>დასრულების დრო</label><input type="time" class="ul w-sm"></div>
      </div>
      <div class="col">
        <div class="fr" style="margin-top:4px;"><label>შედეგი</label>
          <div style="margin-top:6px;display:flex;flex-direction:column;gap:8px;">
            <label style="display:flex;align-items:center;gap:7px;cursor:pointer;font-size:13px;"><input type="radio" name="oq_result" value="ok"> თრომბოლიზისი დასრულდა გართულების გარეშე</label>
            <label style="display:flex;align-items:flex-start;gap:7px;cursor:pointer;font-size:13px;">
              <input type="radio" name="oq_result" value="compl" style="margin-top:3px;"> გართულება:&nbsp;<input type="text" class="ul w-md" placeholder="აღწერეთ">
            </label>
          </div>
        </div>
      </div>
    </div>

    <div class="cols2" style="margin-top:16px;">
      <div class="col">
        <div class="fr"><label>ნევროლოგი</label><input type="text" class="ul w-md doctor-f" data-doc="5" placeholder="სახელი გვარი" oninput="onDoctor(this)"></div>
        <div class="fr" style="margin-top:12px;"><label>ხელმოწერა</label><span class="dash xl"></span></div>
      </div>
      <div class="col">
        <div class="fr"><label>გადაუდებელი დახმარების მედიცინის ექიმი</label><input type="text" class="ul w-md" placeholder="სახელი გვარი"></div>
        <div class="fr" style="margin-top:12px;"><label>ხელმოწერა</label><span class="dash xl"></span></div>
      </div>
    </div>
  </div>
  </div><!-- /doc-5 -->

</div><!-- /viewer -->

<script>
const TITLES = [
  'თანხმობა — 36-ე დადგ. (70%/30%)',
  'თანხმობა — 165-ე დადგ. (90%/10%)',
  'თანხმობა — 218-ე დადგ. (100%)',
  'თანხმობა — კერძო დაზღვევა',
  'სისტემური თრომბოლიზისის სკრინინგი',
  'თრომბოლიზისის ოქმი (მონიტორინგი)'
];

let cur = -1;
let monInit = false;

/* ── Navigation ── */
function openDoc(idx) {
  document.getElementById('toc-screen').style.display = 'none';
  document.getElementById('viewer').style.display = 'block';
  document.querySelectorAll('.doc-page').forEach(d => d.classList.remove('active'));
  document.getElementById('doc-' + idx).classList.add('active');
  cur = idx;
  document.getElementById('vbar-title').textContent = TITLES[idx];

  // sync fields from global
  const p = document.getElementById('g-patient').value;
  const d = document.getElementById('g-doctor').value;
  document.getElementById('b-patient').value = p;
  document.getElementById('b-doctor').value = d;
  fillAll(p, d);

  if (idx === 5 && !monInit) { buildMonTable(); monInit = true; }
  window.scrollTo(0, 0);
}

function showTOC() {
  document.getElementById('viewer').style.display = 'none';
  document.getElementById('toc-screen').style.display = 'flex';
  document.querySelectorAll('.doc-page').forEach(d => d.classList.remove('active'));
  cur = -1;
}

/* ── Field sync ── */
function fillAll(p, d) {
  document.querySelectorAll('.patient-f').forEach(el => { if (!el._focused) el.value = p; });
  document.querySelectorAll('.doctor-f').forEach(el => { if (!el._focused) el.value = d; });
}

function propagate() {
  const p = document.getElementById('g-patient').value;
  const d = document.getElementById('g-doctor').value;
  document.getElementById('b-patient').value = p;
  document.getElementById('b-doctor').value = d;
  fillAll(p, d);
}

function syncBar(type) {
  if (type === 'patient') {
    const v = document.getElementById('b-patient').value;
    document.getElementById('g-patient').value = v;
    document.querySelectorAll('.patient-f').forEach(el => { if (!el._focused) el.value = v; });
  } else {
    const v = document.getElementById('b-doctor').value;
    document.getElementById('g-doctor').value = v;
    document.querySelectorAll('.doctor-f').forEach(el => { if (!el._focused) el.value = v; });
  }
}

function onPatient(el) {
  document.getElementById('g-patient').value = el.value;
  document.getElementById('b-patient').value = el.value;
  document.querySelectorAll('.patient-f').forEach(f => { if (f !== el && !f._focused) f.value = el.value; });
}
function onDoctor(el) {
  document.getElementById('g-doctor').value = el.value;
  document.getElementById('b-doctor').value = el.value;
  document.querySelectorAll('.doctor-f').forEach(f => { if (f !== el && !f._focused) f.value = el.value; });
}

document.addEventListener('focusin', e => { if (e.target.tagName === 'INPUT') e.target._focused = true; });
document.addEventListener('focusout', e => { if (e.target.tagName === 'INPUT') e.target._focused = false; });

/* ── Monitoring table ── */
const MON_ROWS = [
  'საწყისი','+15 წუთი','+15 წუთი','+15 წუთი','+15 წუთი'
];

function buildMonTable() {
  const tb = document.getElementById('mon-body');
  MON_ROWS.forEach(label => appendMonRow(tb, label));
}

function appendMonRow(tb, label) {
  const tr = document.createElement('tr');
  tr.innerHTML = `
    <td>
      <div style="font-size:11px;color:#64748b;margin-bottom:3px;">${label}</div>
      <input placeholder="დრო:" style="margin-bottom:4px;">
      <textarea placeholder="ნევრ. სტატუსი: GCS ___ ქ, NIHSS ___ ქ&#10;კლინიკური სურათი:"></textarea>
    </td>
    <td><input placeholder="მგ/დლ"></td>
    <td>
      <input placeholder="TA:"><input placeholder="HR:">
      <input placeholder="SpO2:"><input placeholder="RR:"><input placeholder="T:">
    </td>
    <td><textarea placeholder="მედიკამენტი / შენიშვნა"></textarea></td>`;
  tb.appendChild(tr);
}

function addMonRow() {
  appendMonRow(document.getElementById('mon-body'), '+15 წუთი');
}

/* ── Print ── */
function doPrint() {
  window.print();
}
</script>
</body>
</html>
