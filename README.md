# 🍽 KampusYemək

**Universitet yeməkxanası üçün onlayn sifariş saytının prototipi.**

Tələbələr fasilədə növbədə gözləmədən yeməyi əvvəlcədən sifariş edir və hazır olanda götürür.

> 📚 **Laboratoriya işi №3** · Fənn: **İnsan-Kompüter İnterfeysi** · Mövzu: **Wireframe və prototip dizaynı**

---

## 📑 Mündəricat

- [Layihə haqqında](#-layihə-haqqında)
- [Problem və həll](#-problem-və-həll)
- [Səhifələr](#-səhifələr)
- [Səhifələr arasında keçid](#-səhifələr-arasında-keçid)
- [İstifadə olunan texnologiyalar](#-i̇stifadə-olunan-texnologiyalar)
- [Fayl strukturu](#-fayl-strukturu)
- [Necə işə salmaq olar](#-necə-işə-salmaq-olar)
- [Dizayn prinsipləri](#-dizayn-prinsipləri)
- [Məhdudiyyətlər](#-məhdudiyyətlər)
- [Gələcək planlar](#-gələcək-planlar)
- [Müəllif](#-müəllif)

---

## 📌 Layihə haqqında

Laboratoriya işinin məqsədi istifadəçi mərkəzli dizayn prinsiplərini tətbiq edərək veb tətbiq üçün ilkin interfeys strukturu hazırlamaqdır. Tapşırıq 4 hissədən ibarətdir:

1. Sadə tətbiq və ya sayt seçmək
2. Əsas səhifələr üçün wireframe (skelet) hazırlamaq
3. Wireframe əsasında kliklənən prototip qurmaq
4. İstifadəçilərdən ilkin rəy toplamaq

Bu layihədə prototip Figma əvəzinə **birbaşa HTML və Bootstrap** ilə hazırlanıb. Belə olanda prototip istənilən brauzerdə işləyir, linklə paylaşmaq olur və sonradan real sayta çevirmək asanlaşır.

Səhifələr bilərəkdən **sadə skelet** formasındadır: şəkil, animasiya və mürəkkəb funksionallıq yoxdur. Diqqət strukturun, naviqasiyanın və istifadəçi axınının üzərindədir.

---

## 🎯 Problem və həll

| | |
|---|---|
| **Problem** | Fasilə qısadır, yeməkxanada isə uzun növbə olur. Tələbələr vaxtlarının çoxunu növbədə keçirir. |
| **Hədəf istifadəçi** | Universitet tələbələri |
| **Həll** | Tələbə menyunu saytda görür, yeməyi səbətə əlavə edir, götürmə vaxtını seçir və hazır yeməyi növbəsiz götürür. |

---

## 🖥 Səhifələr

| Səhifə | Fayl | Məzmun |
|---|---|---|
| **Giriş** | `giris.html` | Tələbə ID (yalnız rəqəm) və şifrə ilə daxil olmaq, qeydiyyata keçid |
| **Qeydiyyat** | `qeydiyyat.html` | Ad-soyad, Tələbə ID (yalnız rəqəm), e-poçt, şifrə və şifrənin təkrarı |
| **Sifariş** | `sifaris.html` | Günün menyusu: axtarış sahəsi və yemək kartları (ad, qiymət, "Səbətə əlavə et") |
| **Səbət** | `sebet.html` | Seçilmiş yeməklər cədvəli (say, qiymət, cəmi), götürmə vaxtı, sifarişin təsdiqi |
| **Əlaqə** | `elaqe.html` | Ünvan, telefon, e-poçt, iş saatları və "Bizə yazın" forması |
| — | `index.html` | Saytın giriş nöqtəsi: avtomatik olaraq Giriş səhifəsinə yönləndirir |

Bütün səhifələrdə eyni struktur var:

```
┌──────────────────────────────────────────────┐
│                 KampusYemək                  │  ← başlıq (header)
│ Sifariş  Səbət  Giriş  Qeydiyyat  Əlaqə      │  ← naviqasiya menyusu
├──────────────────────────────────────────────┤
│                                              │
│              Səhifənin məzmunu               │  ← forma / kartlar / cədvəl
│                                              │
├──────────────────────────────────────────────┤
│ © 2026 KampusYemək. Bütün hüquqlar qorunur.  │  ← alt hissə (footer)
└──────────────────────────────────────────────┘
```

---

## 🔗 Səhifələr arasında keçid

Hər səhifənin menyusundan bütün səhifələrə keçmək olar. Aktiv səhifə menyuda **narıncı** rənglə göstərilir.

Əsas istifadəçi axını:

```
index.html
    │
    ▼
 Giriş ──"Qeydiyyatdan keçin"──► Qeydiyyat
   │  ◄──"Qeydiyyatdan keç" / "Daxil olun"──┘
   │
   │ "Daxil ol"
   ▼
 Sifariş ──"Səbətə əlavə et"──► Səbət
   ▲                              │
   └──"Sifarişi təsdiqlə" / "Menyuya qayıt"──┘
```

| Səhifə | Düymə / link | Hara aparır |
|---|---|---|
| Giriş | Daxil ol | Sifariş |
| Giriş | Qeydiyyatdan keçin | Qeydiyyat |
| Qeydiyyat | Qeydiyyatdan keç | Giriş |
| Qeydiyyat | Daxil olun | Giriş |
| Sifariş | Səbətə əlavə et | Səbət |
| Səbət | Sifarişi təsdiqlə | Sifariş |
| Səbət | Menyuya qayıt | Sifariş |
| Əlaqə | Göndər | Əlaqə |

---

## 🛠 İstifadə olunan texnologiyalar

| Texnologiya | Nə üçün |
|---|---|
| **HTML5** | Səhifələrin strukturu |
| **CSS3** | Naviqasiya və footer üçün öz stillərimiz (`style.css`) |
| **[Bootstrap 5.3](https://getbootstrap.com/)** | Hazır grid sistemi, formalar, kartlar, cədvəllər və düymələr (CDN ilə qoşulub) |
| **Git + GitHub** | Versiya nəzarəti və kodun saxlanması |
| **Netlify** | Saytın pulsuz yerləşdirilməsi (hosting) |

JavaScript istifadə olunmayıb. Formaların yoxlanması (boş sahə, e-poçt formatı, Tələbə ID-nin yalnız rəqəm olması) HTML5-in öz imkanları ilə edilir: `required`, `type="email"`, `pattern="[0-9]+"`.

---

## 📁 Fayl strukturu

```
kampusyemek/
├── index.html        # Giriş nöqtəsi → giris.html səhifəsinə yönləndirir
├── giris.html        # Giriş səhifəsi
├── qeydiyyat.html    # Qeydiyyat səhifəsi
├── sifaris.html      # Menyu və sifariş səhifəsi
├── sebet.html        # Səbət və sifarişin təsdiqi
├── elaqe.html        # Əlaqə səhifəsi
├── style.css         # Ortaq stillər (naviqasiya, footer, linklər)
└── README.md         # Bu sənəd
```

---

## 🚀 Necə işə salmaq olar

### 1. Kompüterdə

Heç nə quraşdırmaq lazım deyil:

1. Repo-nu yüklə: **Code → Download ZIP** və ya:
   ```bash
   git clone https://github.com/VaqifIbrahimli/kampusyemek.git
   ```
2. Qovluqdakı `index.html` faylına iki dəfə kliklə. Sayt brauzerdə açılacaq.

> ℹ️ Bootstrap internetdən (CDN) yüklənir. İnternet olmasa, səhifələr açılır, amma dizaynsız görünür.

### 2. Netlify-da (onlayn)

1. [app.netlify.com](https://app.netlify.com) saytına GitHub hesabı ilə daxil ol.
2. **Add new site → Import an existing project → GitHub** seç.
3. `kampusyemek` repo-sunu seç.
4. Ayarlar:
   - **Build command:** *(boş burax)*
   - **Publish directory:** `.`
5. **Deploy** bas.

Bundan sonra repo-ya edilən hər `git push` saytı avtomatik yeniləyir.

---

## 🎨 Dizayn prinsipləri

Prototipdə İnsan-Kompüter İnterfeysinin aşağıdakı prinsipləri tətbiq olunub:

| Prinsip | Saytda necə tətbiq olunub |
|---|---|
| **Ardıcıllıq (Consistency)** | Bütün səhifələrdə eyni header, menyu, footer, rəng və düymə üslubu var. İstifadəçi hər səhifədə harada olduğunu dərhal anlayır. |
| **Görünən vəziyyət (Visibility of system status)** | Menyuda aktiv səhifə narıncı rənglə seçilir. |
| **Sadəlik (Minimalism)** | Hər səhifədə yalnız lazım olan elementlər var. Lazımsız şəkil və bəzək yoxdur. |
| **Səhvlərin qarşısını almaq (Error prevention)** | Tələbə ID yalnız rəqəm qəbul edir, e-poçt formatı yoxlanılır, boş sahə ilə forma göndərilmir. |
| **Tanımaq, xatırlamaqdan yaxşıdır (Recognition over recall)** | Hər sahənin üstündə aydın etiket (label), içində isə nümunə mətn (placeholder) var. |
| **İstifadəçi nəzarəti (User control)** | Səbətdə "Menyuya qayıt" düyməsi var. Giriş və qeydiyyat səhifələri bir-birinə link verir. |
| **Uyğunlaşan dizayn (Responsive)** | Bootstrap grid sayəsində sayt həm kompüterdə, həm telefonda düzgün görünür. |
| **Kontrast və oxunaqlılıq** | Tünd boz (`#212529`) fon üzərində ağ mətn, aktiv element üçün narıncı (`#FFA500`) vurğu. |

---

## ⚠️ Məhdudiyyətlər

Bu, **prototipdir**, işləyən sistem deyil:

- Server və verilənlər bazası yoxdur. Qeydiyyat və giriş məlumatları heç yerdə saxlanılmır və yoxlanılmır.
- Səbətdəki yeməklər sabit nümunədir. "Səbətə əlavə et" düyməsi yalnız Səbət səhifəsinə keçid edir.
- Axtarış sahəsi vizual elementdir, hələ işləmir.
- Əlaqə səhifəsindəki telefon və e-poçt nümunədir.

---

## 🔮 Gələcək planlar

- [ ] JavaScript ilə işləyən səbət (yemək əlavə etmək və çıxarmaq, cəmin avtomatik hesablanması)
- [ ] İşləyən axtarış və kateqoriya filtrləri
- [ ] Backend və verilənlər bazası ilə real qeydiyyat və giriş (şifrələrin heş edilərək saxlanması)
- [ ] Sifariş nömrəsi və "sifarişiniz hazırdır" bildirişi
- [ ] Yemək şəkilləri və ətraflı məlumat (kalori, tərkib)
- [ ] İstifadəçi rəyləri əsasında interfeysin təkmilləşdirilməsi

---

## 👤 Müəllif

**Vaqif İbrahimli**
GitHub: [@VaqifIbrahimli](https://github.com/VaqifIbrahimli)

---

<sub>© 2026 KampusYemək · İnsan-Kompüter İnterfeysi fənni üzrə laboratoriya işi</sub>
