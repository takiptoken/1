<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>TakipToken | Dashboard</title>

  <!-- Tailwind + Dark Mode -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = { darkMode: 'class' };
  </script>

  <!-- Google Font & Icons -->
  <link 
    href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" 
    rel="stylesheet"
  />
  <link 
    rel="stylesheet" 
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css"
  />

  <style>
    body { font-family: 'Poppins', sans-serif; }
  </style>
</head>
<body class="flex h-screen bg-gray-100 dark:bg-gray-900 text-gray-800 dark:text-gray-200">

  <!-- SIDEBAR -->
  <aside class="w-64 bg-white dark:bg-gray-800 shadow flex-shrink-0">
    <div class="p-4 flex items-center space-x-3">
      <img id="profile-pic" src="" alt="Profil" class="w-10 h-10 rounded-full bg-gray-200"/>
      <div>
        <p id="profile-name" class="font-semibold">Kullanıcı</p>
        <button id="sign-out" class="text-xs text-red-500 hover:underline">Çıkış Yap</button>
      </div>
    </div>
    <nav class="mt-4">
      <ul id="menu" class="space-y-1">
        <li><a data-section="home"    href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Ana Sayfa</a></li>
        <li><a data-section="report"  href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Bildir</a></li>
        <li><a data-section="create"  href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Görev Oluştur</a></li>
        <li><a data-section="pending" href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Bekleyen Kanıtlar</a></li>
        <li><a data-section="survey"  href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Anketler</a></li>
        <li><a data-section="bonus"   href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Günlük Bonus</a></li>
        <li><a data-section="chest"   href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Kasa Sistemi</a></li>
        <li><a data-section="events"  href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Etkinlikler</a></li>
        <li><a data-section="chat"    href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Sohbet</a></li>
        <li><a data-section="tasks"   href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Görevlerim</a></li>
        <li><a data-section="rank"    href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Rank</a></li>
        <li><a data-section="support" href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Destek</a></li>
        <li><a data-section="referral"href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Referans Sistemi</a></li>
        <li><a data-section="faq"     href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">S.S.S.</a></li>
        <li><a data-section="blog"    href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded">Blog</a></li>
        <li id="admin-menu" class="hidden"><a data-section="admin" href="#" class="nav-link block px-4 py-2 hover:bg-gray-200 dark:hover:bg-gray-700 rounded text-red-600">Admin Panel</a></li>
      </ul>
    </nav>
    <div class="mt-auto p-4">
      <button id="dark-toggle" class="w-full px-2 py-1 bg-gray-200 dark:bg-gray-700 rounded hover:bg-gray-300 dark:hover:bg-gray-600 transition">
        <i id="dark-icon" class="fas fa-moon"></i> Dark
      </button>
    </div>
  </aside>

  <!-- MAIN -->
  <div class="flex-1 flex flex-col overflow-hidden">
    <header class="flex items-center justify-between bg-white dark:bg-gray-800 px-6 py-4 shadow">
      <h1 id="section-title" class="text-xl font-semibold">Ana Sayfa</h1>
    </header>

    <main class="flex-1 overflow-y-auto p-6 space-y-6">
      <!-- Her bölüm burada, varsayılan home görünür -->
      <section id="home"    class="section active"><h2 class="text-2xl">Ana Sayfa</h2></section>
      <section id="report"  class="section hidden"><h2 class="text-2xl">Bildir</h2></section>
      <section id="create"  class="section hidden">
        <h2 class="text-2xl mb-4">Görev Oluştur</h2>
        <form id="create-task-form" class="space-y-4 max-w-lg">
          <div>
            <label class="block mb-1 font-medium">Başlık</label>
            <input type="text" id="task-title" required class="w-full px-3 py-2 border rounded focus:outline-none focus:ring-2 focus:ring-green-500" placeholder="Görev başlığı">
          </div>
          <div>
            <label class="block mb-1 font-medium">Açıklama</label>
            <textarea id="task-desc" required class="w-full px-3 py-2 border rounded focus:outline-none focus:ring-2 focus:ring-green-500" placeholder="Görev açıklaması"></textarea>
          </div>
          <div>
            <label class="block mb-1 font-medium">Platform</label>
            <select id="task-platform" required class="w-full px-3 py-2 border rounded focus:outline-none focus:ring-2 focus:ring-green-500">
              <option value="">Seçiniz</option>
              <option>Instagram</option>
              <option>YouTube</option>
              <option>TikTok</option>
              <option>Twitter</option>
            </select>
          </div>
          <div>
            <label class="block mb-1 font-medium">Token Miktarı</label>
            <input type="number" id="task-token" min="1" required class="w-full px-3 py-2 border rounded focus:outline-none focus:ring-2 focus:ring-green-500" placeholder="Örn: 5">
          </div>
          <div class="flex items-center gap-2">
            <input type="checkbox" id="task-proof" class="h-4 w-4">
            <label for="task-proof" class="text-sm">Kanıt yüklemesi istensin</label>
          </div>
          <button type="submit" class="px-4 py-2 bg-green-600 text-white rounded hover:bg-green-700 transition">Görev Oluştur</button>
          <p id="create-task-msg" class="text-sm mt-2"></p>
        </form>
      </section>
      <section id="pending" class="section hidden"><h2 class="text-2xl">Bekleyen Kanıtlar</h2></section>
      <section id="survey"  class="section hidden"><h2 class="text-2xl">Anketler</h2></section>
      <section id="bonus" class="section hidden">
        <h2 class="text-2xl mb-4">Günlük Bonus</h2>
        <div class="bg-white dark:bg-gray-800 p-6 rounded shadow max-w-md mx-auto flex flex-col items-center">
          <div id="bonus-status" class="mb-4 text-center text-lg font-semibold">Her gün giriş yap, bonus token kazan!</div>
          <button id="get-bonus-btn" class="px-6 py-3 bg-green-600 text-white rounded-lg text-lg font-bold hover:bg-green-700 transition mb-2">Bonus Al</button>
          <div id="bonus-result" class="mt-4 text-xl font-bold text-green-600"></div>
        </div>
      </section>
      <section id="chest" class="section hidden">
        <h2 class="text-2xl mb-4">Kasa Sistemi</h2>
        <div class="bg-white dark:bg-gray-800 p-6 rounded shadow max-w-md mx-auto flex flex-col items-center">
          <div id="chest-status" class="mb-4 text-center text-lg font-semibold">7 gün üst üste giriş yap, kasayı aç!</div>
          <button id="open-chest-btn" class="px-6 py-3 bg-yellow-500 text-white rounded-lg text-lg font-bold hover:bg-yellow-600 transition mb-2">Kasa Aç</button>
          <div id="chest-result" class="mt-4 text-xl font-bold text-green-600"></div>
        </div>
      </section>
      <section id="tasks"   class="section hidden">
        <h2 class="text-2xl mb-4">Görevlerim</h2>
        <div id="tasks-list" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4"></div>
        <div id="tasks-empty" class="text-gray-500 mt-8 hidden">Hiç görev bulunamadı.</div>
      </section>
      <section id="events" class="section hidden">
        <h2 class="text-2xl mb-4">Etkinlikler</h2>
        <div id="events-list" class="space-y-4"></div>
        <div id="events-empty" class="text-gray-500 mt-8 hidden">Şu anda etkinlik yok.</div>
      </section>
      <section id="chat" class="section hidden">
        <h2 class="text-2xl mb-4">Genel Sohbet</h2>
        <div class="bg-white dark:bg-gray-800 p-4 rounded shadow max-w-2xl mx-auto flex flex-col h-[400px]">
          <div id="chat-messages" class="flex-1 overflow-y-auto space-y-2 mb-4"></div>
          <form id="chat-form" class="flex gap-2">
            <input id="chat-input" type="text" class="flex-1 px-3 py-2 border rounded focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Mesaj yaz..." autocomplete="off" required />
            <button type="submit" class="px-4 py-2 bg-indigo-600 text-white rounded hover:bg-indigo-700 transition">Gönder</button>
          </form>
        </div>
      </section>
      <section id="rank" class="section hidden">
        <h2 class="text-2xl mb-4">Rank Sistemi</h2>
        <div class="bg-white dark:bg-gray-800 p-6 rounded shadow max-w-md mx-auto flex flex-col items-center">
          <div id="rank-level" class="text-3xl font-bold mb-2">Demir</div>
          <div id="rank-progress" class="w-full bg-gray-200 dark:bg-gray-700 rounded h-4 mb-2">
            <div id="rank-bar" class="bg-yellow-400 h-4 rounded" style="width: 10%"></div>
          </div>
          <div id="rank-info" class="text-gray-600 dark:text-gray-300">Tamamlanan görev: <span id="rank-tasks">0</span></div>
        </div>
      </section>
      <section id="support" class="section hidden"><h2 class="text-2xl">Destek</h2></section>
      <section id="support" class="section hidden">
        <h2 class="text-2xl mb-4">Destek</h2>
        <div class="bg-white dark:bg-gray-800 p-6 rounded shadow max-w-md mx-auto">
          <div class="mb-2">Bize ulaşmak için:</div>
          <ul class="mb-4 space-y-1">
            <li><b>WhatsApp:</b> <a href="https://wa.me/905555555555" class="text-green-600 underline">+90 555 555 55 55</a></li>
            <li><b>E-posta:</b> <a href="mailto:destek@takiptoken.com" class="text-blue-600 underline">destek@takiptoken.com</a></li>
            <li><b>Telegram:</b> <a href="https://t.me/takiptoken" class="text-blue-500 underline">@takiptoken</a></li>
          </ul>
          <form id="support-form" class="space-y-2">
            <textarea id="support-msg" class="w-full px-3 py-2 border rounded" placeholder="Sorunuzu yazın..." required></textarea>
            <button type="submit" class="px-4 py-2 bg-indigo-600 text-white rounded hover:bg-indigo-700 transition">Destek Talebi Gönder</button>
            <div id="support-result" class="text-green-600 mt-2"></div>
          </form>
        </div>
      </section>
      <section id="referral"class="section hidden"><h2 class="text-2xl">Referans Sistemi</h2></section>
      <section id="referral" class="section hidden">
        <h2 class="text-2xl mb-4">Referans Sistemi</h2>
        <div class="bg-white dark:bg-gray-800 p-6 rounded shadow max-w-md mx-auto flex flex-col items-center">
          <div class="mb-2">Senin referans kodun:</div>
          <div id="ref-code" class="font-mono text-lg bg-gray-100 dark:bg-gray-700 px-4 py-2 rounded mb-2 select-all">TTK-12345</div>
          <button id="copy-ref-btn" class="mb-4 px-3 py-1 bg-blue-600 text-white rounded hover:bg-blue-700 transition">Kodu Kopyala</button>
          <div class="w-full mt-4">
            <div class="font-semibold mb-2">Davet Ettiklerin</div>
            <ul id="ref-list" class="list-disc pl-6 text-gray-700 dark:text-gray-300"></ul>
            <div id="ref-empty" class="text-gray-500 mt-2">Henüz kimseyi davet etmedin.</div>
          </div>
        </div>
      </section>
      <section id="faq"     class="section hidden"><h2 class="text-2xl">S.S.S.</h2></section>
      <section id="faq" class="section hidden">
        <h2 class="text-2xl mb-4">Sıkça Sorulan Sorular</h2>
        <div id="faq-list" class="space-y-4"></div>
        <form id="faq-form" class="mt-6 space-y-2 max-w-lg">
          <input id="faq-q" type="text" class="w-full px-3 py-2 border rounded" placeholder="Yeni soru ekle..." required />
          <button type="submit" class="px-4 py-2 bg-green-600 text-white rounded hover:bg-green-700 transition">Soru Gönder</button>
          <div id="faq-result" class="text-green-600 mt-2"></div>
        </form>
      </section>
      <section id="blog"    class="section hidden"><h2 class="text-2xl">Blog</h2></section>
      <section id="blog" class="section hidden">
        <h2 class="text-2xl mb-4">Blog</h2>
        <div id="blog-list" class="space-y-4"></div>
      </section>
      <section id="admin" class="section hidden">
        <h2 class="text-2xl mb-4 text-red-600">Admin Panel</h2>
        <div class="bg-white dark:bg-gray-800 p-6 rounded shadow max-w-lg mx-auto">
          <div class="mb-4">Yalnızca admin kullanıcılar görebilir.<br>
            <span class="text-xs text-gray-500">Admin panelini görmek için kendi UID'nizi <b>setupAdminPanel</b> fonksiyonundaki <b>adminUIDs</b> dizisine ekleyin.</span>
          </div>
          <div class="mb-2 font-semibold">Kullanıcı Yönetimi (Demo)</div>
          <ul id="admin-users" class="mb-4 space-y-1"></ul>
          <div class="mb-2 font-semibold">Görev Moderasyonu (Demo)</div>
          <ul id="admin-tasks" class="space-y-1"></ul>
        </div>
      </section>
    </main>
  </div>

  <!-- Firebase + Uygulama JS -->
  <script type="module">
    import { initializeApp }   from "https://www.gstatic.com/firebasejs/9.23.0/firebase-app.js";
    import { getAuth,
             onAuthStateChanged,
             signOut }          from "https://www.gstatic.com/firebasejs/9.23.0/firebase-auth.js";
    import { getFirestore }    from "https://www.gstatic.com/firebasejs/9.23.0/firebase-firestore.js";

    // 1) Firebase config ve init
   const firebaseConfig = {
      apiKey: "AIzaSyC7lRIhanhgv_2BLgjIA_F0D04vRAaA5uk",
      authDomain: "takiptoken-4c1fa.firebaseapp.com",
      projectId: "takiptoken-4c1fa",
      storageBucket: "takiptoken-4c1fa.appspot.com",
      messagingSenderId: "518688622476",
      appId: "1:518688622476:web:8757ec47fb2614836738a9",
      measurementId: "G-EYNR6Z8JTV"
    };
    const app  = initializeApp(firebaseConfig);
    const auth = getAuth(app);
    const db   = getFirestore(app);

    // 2) DOM referansları
    const menuLinks     = document.querySelectorAll(".nav-link");
    const sections      = document.querySelectorAll(".section");
    const titleEl       = document.getElementById("section-title");
    const picEl         = document.getElementById("profile-pic");
    const nameEl        = document.getElementById("profile-name");
    const signOutBtn    = document.getElementById("sign-out");
    const darkToggle    = document.getElementById("dark-toggle");
    const darkIcon      = document.getElementById("dark-icon");

    // 3) Sekme tıklama handler
    menuLinks.forEach(link => {
      link.addEventListener("click", e => {
        e.preventDefault();
        // link’i aktifleştir
        menuLinks.forEach(l => l.classList.remove("bg-gray-200","dark:bg-gray-700"));
        link.classList.add("bg-gray-200","dark:bg-gray-700");
        // section göster
        const sec = link.dataset.section;
        sections.forEach(s => s.id === sec ? s.classList.remove("hidden") : s.classList.add("hidden"));
        // başlığı değiştir
        titleEl.innerText = link.innerText.trim();
      });
    });

    // 4) Dark mode toggle
    if (localStorage.theme === "dark") document.documentElement.classList.add("dark");
    darkToggle.addEventListener("click", () => {
      document.documentElement.classList.toggle("dark");
      const isDark = document.documentElement.classList.contains("dark");
      localStorage.theme = isDark ? "dark" : "light";
      darkIcon.className = isDark ? "fas fa-sun" : "fas fa-moon";
    });

    // 5) Auth ve profil bilgisi yükle
    onAuthStateChanged(auth, user => {
      if (!user) return location.href = "login.html";
      // Profil fotoğrafı ve isim
      picEl.src       = user.photoURL || "https://via.placeholder.com/40";
      nameEl.innerText= user.displayName || user.email;

      // Çıkış
      signOutBtn.addEventListener("click", () => {
        signOut(auth).then(() => location.href = "login.html");
      });

      // --- Görevler Modülü ---
      loadUserTasks(user.uid);
      // --- Görev Oluştur Modülü ---
      setupCreateTask(user.uid);
      // --- Kasa Sistemi Modülü ---
      setupChestSystem(user.uid);
      // --- Etkinlikler Modülü ---
      loadEvents();
      // --- Sohbet Modülü ---
      setupChat(user);
      // --- Günlük Bonus Modülü ---
      setupDailyBonus(user.uid);
      // --- Rank Sistemi Modülü ---
      setupRankSystem(user.uid);
      // --- Referans Sistemi Modülü ---
      setupReferralSystem(user);
      // --- Destek Modülü ---
      setupSupport();
      // --- SSS Modülü ---
      setupFAQ();
      // --- Blog Modülü ---
      setupBlog();

      // --- Admin Panel Modülü ---
      setupAdminPanel(user);
// Admin Panel modülü: Sadece adminler için göster
function setupAdminPanel(user) {
  const adminMenu = document.getElementById("admin-menu");
  const adminSection = document.getElementById("admin");
  if (!adminMenu || !adminSection) return;
  // Demo: Sadece belirli UID admin kabul edilir
  const adminUIDs = ["adminUID1", "adminUID2"];
  if (!adminUIDs.includes(user.uid)) {
    adminMenu.classList.add("hidden");
    adminSection.classList.add("hidden");
    return;
  }
  adminMenu.classList.remove("hidden");
  // Demo kullanıcı listesi
  const users = [
    { name: "Ali", email: "ali@mail.com", banned: false },
    { name: "Ayşe", email: "ayse@mail.com", banned: true }
  ];
  const userList = document.getElementById("admin-users");
  userList.innerHTML = "";
  users.forEach(u => {
    const li = document.createElement("li");
    li.innerHTML = `<b>${u.name}</b> (${u.email}) ${u.banned ? "<span class=\"text-red-600\">(Banlı)</span>" : ""}`;
    userList.appendChild(li);
  });
  // Demo görev listesi
  const tasks = [
    { title: "Instagram Takip", owner: "ali@mail.com", status: "Onay Bekliyor" },
    { title: "YouTube Yorum", owner: "ayse@mail.com", status: "Yayında" }
  ];
  const taskList = document.getElementById("admin-tasks");
  taskList.innerHTML = "";
  tasks.forEach(t => {
    const li = document.createElement("li");
    li.innerHTML = `<b>${t.title}</b> - ${t.owner} <span class=\"text-gray-500\">(${t.status})</span>`;
    taskList.appendChild(li);
  });
}
    });

// Görevler modülü: Firestore'dan görevleri çek ve göster
async function loadUserTasks(uid) {
  const tasksList = document.getElementById("tasks-list");
  const tasksEmpty = document.getElementById("tasks-empty");
  tasksList.innerHTML = "";
  tasksEmpty.classList.add("hidden");

  // Firestore'dan görevleri çek (örnek veri ile başlat)
  // TODO: Firestore entegrasyonu
  // const q = query(collection(db, "tasks"), where("owner", "==", uid));
  // const snap = await getDocs(q);
  // if (snap.empty) { ... }

  // Şimdilik örnek veri:
  const exampleTasks = [
    { id: 1, platform: "Instagram", user: "@kullanici1", desc: "Takip et!", token: 5, proof: true },
    { id: 2, platform: "YouTube", user: "@kanal2", desc: "Yoruma katıl!", token: 8, proof: false }
  ];
  if (exampleTasks.length === 0) {
    tasksEmpty.classList.remove("hidden");
    return;
  }
  exampleTasks.forEach(task => {
    const div = document.createElement("div");
    div.className = "bg-white dark:bg-gray-800 p-4 rounded shadow flex flex-col gap-2";
    div.innerHTML = `
      <div class="flex items-center gap-2">
        <span class="font-bold">${task.platform}</span>
        <span class="text-gray-400">${task.user}</span>
      </div>
      <div>${task.desc}</div>
      <div class="flex items-center gap-2 mt-2">
        <span class="text-green-600 font-semibold">+${task.token} Token</span>
        ${task.proof ? '<span class="text-xs bg-yellow-100 text-yellow-700 px-2 py-1 rounded">Kanıt İsteniyor</span>' : ''}
      </div>
      <button class="mt-2 px-3 py-1 bg-blue-600 text-white rounded hover:bg-blue-700 transition">Görevi Tamamla</button>
    `;
    tasksList.appendChild(div);
  });
}

// Görev Oluştur modülü: Form submit işlemi
function setupCreateTask(uid) {
  const form = document.getElementById("create-task-form");
  const msg = document.getElementById("create-task-msg");
  if (!form) return;
  form.addEventListener("submit", async e => {
    e.preventDefault();
    msg.textContent = "";
    const title = document.getElementById("task-title").value.trim();
    const desc = document.getElementById("task-desc").value.trim();
    const platform = document.getElementById("task-platform").value;
    const token = parseInt(document.getElementById("task-token").value, 10);
    const proof = document.getElementById("task-proof").checked;

    if (!title || !desc || !platform || !token) {
      msg.textContent = "Tüm alanları doldurun.";
      msg.className = "text-red-600 mt-2";
      return;
    }

    // TODO: Firestore'a ekle
    // await addDoc(collection(db, "tasks"), { owner: uid, title, desc, platform, token, proof, done: false, created: Date.now() });

    msg.textContent = "Görev başarıyla oluşturuldu! (Demo)";
    msg.className = "text-green-600 mt-2";
    form.reset();
  });
}

// Kasa Sistemi modülü: Demo kasa açma
function setupChestSystem(uid) {
  const openBtn = document.getElementById("open-chest-btn");
  const result = document.getElementById("chest-result");
  const status = document.getElementById("chest-status");
  if (!openBtn) return;
  openBtn.addEventListener("click", () => {
    // Demo: Rastgele ödül
    const rewards = [
      { type: "token", value: Math.floor(Math.random()*50+10) },
      { type: "premium", value: 1 },
      { type: "bonus", value: 1 },
      { type: "special", value: 1 }
    ];
    const reward = rewards[Math.floor(Math.random()*rewards.length)];
    let msg = "";
    if (reward.type === "token") msg = `🎉 ${reward.value} Token kazandın!`;
    if (reward.type === "premium") msg = `⭐ 1 Gün Premium Üyelik!`;
    if (reward.type === "bonus") msg = `🎁 Bonus Kasa kazandın!`;
    if (reward.type === "special") msg = `📝 Özel Görev Hakkı!`;
    result.textContent = msg;
    status.textContent = "Kasa açıldı! Yarın tekrar dene.";
    openBtn.disabled = true;
    openBtn.classList.add("opacity-50");
  });
}

// Etkinlikler modülü: Demo etkinlik listesi ve katılım
function loadEvents() {
  const eventsList = document.getElementById("events-list");
  const eventsEmpty = document.getElementById("events-empty");
  eventsList.innerHTML = "";
  eventsEmpty.classList.add("hidden");

  // Demo etkinlikler
  const demoEvents = [
    { id: 1, title: "Instagram Takip Etkinliği", desc: "Herkes birbirini takip ediyor!", reward: "+20 Token", joined: false },
    { id: 2, title: "YouTube Yorum Maratonu", desc: "En çok yorum yapan kazanır!", reward: "+30 Token", joined: false }
  ];
  if (demoEvents.length === 0) {
    eventsEmpty.classList.remove("hidden");
    return;
  }
  demoEvents.forEach(event => {
    const div = document.createElement("div");
    div.className = "bg-white dark:bg-gray-800 p-4 rounded shadow flex flex-col gap-2";
    div.innerHTML = `
      <div class="flex items-center gap-2">
        <span class="font-bold text-lg">${event.title}</span>
        <span class="text-green-600 font-semibold ml-auto">${event.reward}</span>
      </div>
      <div>${event.desc}</div>
      <button class="mt-2 px-3 py-1 bg-indigo-600 text-white rounded hover:bg-indigo-700 transition join-event-btn">Katıl</button>
    `;
    const btn = div.querySelector(".join-event-btn");
    btn.addEventListener("click", () => {
      btn.disabled = true;
      btn.textContent = "Katıldın!";
      btn.classList.add("bg-green-600");
      setTimeout(() => {
        btn.textContent = "Etkinlik Başladı!";
      }, 2000);
    });
    eventsList.appendChild(div);
  });
}

// Sohbet modülü: Demo mesajlaşma
function setupChat(user) {
  const chatForm = document.getElementById("chat-form");
  const chatInput = document.getElementById("chat-input");
  const chatMessages = document.getElementById("chat-messages");
  if (!chatForm) return;

  // Demo mesajlar
  const demoMsgs = [
    { name: "Admin", text: "Hoş geldiniz!" },
    { name: "Kullanıcı1", text: "Merhaba 👋" }
  ];
  chatMessages.innerHTML = "";
  demoMsgs.forEach(msg => {
    const div = document.createElement("div");
    div.className = "p-2 rounded bg-gray-100 dark:bg-gray-700";
    div.innerHTML = `<b>${msg.name}:</b> ${msg.text}`;
    chatMessages.appendChild(div);
  });

  chatForm.addEventListener("submit", e => {
    e.preventDefault();
    const val = chatInput.value.trim();
    if (!val) return;
    const div = document.createElement("div");
    div.className = "p-2 rounded bg-indigo-100 dark:bg-indigo-700 text-indigo-900 dark:text-white";
    div.innerHTML = `<b>${user.displayName || user.email}:</b> ${val}`;
    chatMessages.appendChild(div);
    chatInput.value = "";
    chatMessages.scrollTop = chatMessages.scrollHeight;
  });
}

// Günlük Bonus modülü: Demo bonus alma
function setupDailyBonus(uid) {
  const bonusBtn = document.getElementById("get-bonus-btn");
  const bonusResult = document.getElementById("bonus-result");
  const bonusStatus = document.getElementById("bonus-status");
  if (!bonusBtn) return;
  bonusBtn.addEventListener("click", () => {
    // Demo: Rastgele bonus
    const amount = Math.floor(Math.random()*5+1);
    bonusResult.textContent = `🎉 ${amount} Token kazandın!`;
    bonusStatus.textContent = "Yarın tekrar gel!";
    bonusBtn.disabled = true;
    bonusBtn.classList.add("opacity-50");
  });
}

// Rank Sistemi modülü: Demo rank hesaplama
function setupRankSystem(uid) {
  const levelEl = document.getElementById("rank-level");
  const barEl = document.getElementById("rank-bar");
  const infoEl = document.getElementById("rank-tasks");
  if (!levelEl) return;
  // Demo: Tamamlanan görev sayısına göre rank
  const completed = Math.floor(Math.random()*20+1);
  infoEl.textContent = completed;
  let level = "Demir", percent = 5;
  if (completed >= 5)  { level = "Bakır"; percent = 25; }
  if (completed >= 10) { level = "Çelik"; percent = 50; }
  if (completed >= 15) { level = "Altın"; percent = 75; }
  if (completed >= 20) { level = "Elmas"; percent = 100; }
  levelEl.textContent = level;
  barEl.style.width = percent + "%";
}

// Referans Sistemi modülü: Demo referans kodu ve davetli listesi
function setupReferralSystem(user) {
  const codeEl = document.getElementById("ref-code");
  const copyBtn = document.getElementById("copy-ref-btn");
  const listEl = document.getElementById("ref-list");
  const emptyEl = document.getElementById("ref-empty");
  if (!codeEl) return;
  // Demo kodu ve davetliler
  const code = "TTK-" + (user.uid ? user.uid.slice(0,5).toUpperCase() : "12345");
  codeEl.textContent = code;
  copyBtn.onclick = () => {
    navigator.clipboard.writeText(code);
    copyBtn.textContent = "Kopyalandı!";
    setTimeout(() => copyBtn.textContent = "Kodu Kopyala", 1500);
  };
  // Demo davetli listesi
  const invited = ["ali@mail.com", "ayse@mail.com"];
  listEl.innerHTML = "";
  if (invited.length === 0) {
    emptyEl.classList.remove("hidden");
  } else {
    emptyEl.classList.add("hidden");
    invited.forEach(mail => {
      const li = document.createElement("li");
      li.textContent = mail;
      listEl.appendChild(li);
    });
  }
}

// Destek modülü: Demo destek talebi
function setupSupport() {
  const form = document.getElementById("support-form");
  const msg = document.getElementById("support-msg");
  const result = document.getElementById("support-result");
  if (!form) return;
  form.addEventListener("submit", e => {
    e.preventDefault();
    result.textContent = "Talebiniz alındı! (Demo)";
    msg.value = "";
    setTimeout(() => result.textContent = "", 2000);
  });
}

// SSS modülü: Demo soru-cevap
function setupFAQ() {
  const faqList = document.getElementById("faq-list");
  const faqForm = document.getElementById("faq-form");
  const faqQ = document.getElementById("faq-q");
  const faqResult = document.getElementById("faq-result");
  if (!faqList) return;
  // Demo sorular
  const faqs = [
    { q: "Token nasıl kazanılır?", a: "Görevleri tamamlayarak token kazanabilirsin." },
    { q: "Premium nedir?", a: "Premium üyeler ekstra avantajlara sahip olur." }
  ];
  faqList.innerHTML = "";
  faqs.forEach(faq => {
    const div = document.createElement("div");
    div.className = "bg-gray-100 dark:bg-gray-700 p-3 rounded";
    div.innerHTML = `<b>${faq.q}</b><br><span>${faq.a}</span>`;
    faqList.appendChild(div);
  });
  faqForm.addEventListener("submit", e => {
    e.preventDefault();
    faqResult.textContent = "Sorun alındı, admin onayından sonra yayınlanacak. (Demo)";
    faqQ.value = "";
    setTimeout(() => faqResult.textContent = "", 2000);
  });
}

// Blog modülü: Demo blog postları
function setupBlog() {
  const blogList = document.getElementById("blog-list");
  if (!blogList) return;
  // Demo bloglar
  const blogs = [
    { title: "TakipToken Nedir?", content: "TakipToken, sosyal medya görevleriyle token kazanmanı sağlar.", date: "2025-07-01" },
    { title: "Token Kazanma İpuçları", content: "Görevleri düzenli tamamla, bonusları kaçırma!", date: "2025-07-15" }
  ];
  blogList.innerHTML = "";
  blogs.forEach(blog => {
    const div = document.createElement("div");
    div.className = "bg-white dark:bg-gray-700 p-4 rounded shadow";
    div.innerHTML = `<div class='text-lg font-bold mb-1'>${blog.title}</div><div class='text-gray-500 text-sm mb-2'>${blog.date}</div><div>${blog.content}</div>`;
    blogList.appendChild(div);
  });
}
  </script>
</body>
</html>
