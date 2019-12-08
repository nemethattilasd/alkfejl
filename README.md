<H1>Alkalmazások fejlesztése beadandó</H1>
<H3>Bevezető</H3>
<p>Az alapötlet a neptun mintájára épülő, az egyetem szereplői számára adminisztrációs feladatok(tantárgyak felvétele/menedzselése tanároknak/diákoknak) kezelésére alkalmas program létrehozása.</p>
<H2>Követelményanalízis</H2>
<H3>Funkcionális követelmények</H3>
<ul>
  <li>Regisztráció</li>
  <li>Bejelentkezés</li>
  <li>Bejelentkezett felhasználóknak
    <ul>
      <li>Tanárnak</li>
        <ul>
          <li>Saját kurzusok törlése/megjelenítése órarendben</li> 
          <li>Saját vizsgák törlése/megjelenítése órarendben</li> 
          <li>Kurzusok/Vizsgák kilistázása</li>
        </ul>
      <li>Diáknak</li>
        <ul>
          <li>Kurzus felvétele/leadása</li>
          <li>Vizsga felvétele/leadása</li>
          <li>Kurzusok/Vizsgák kilistázása</li>
        </ul>
    </ul>
  </li>
</ul>
<H3>Nem funkcionális követelmények</H3>
<ul>
  <li>Felhasználóbarát: Megfelelően elhatárolt funkciók. Világos látható színekkel írt betűk. Ésszerű elrendezés.</li>
  <li>Biztonság: Jelszóval védett funkciók. A jelszavak titkosítottak. A különböző űrlapoknál egy hibalistában kijelzi a program a hibákat.</li>
  <li>Gyors működés: Adatbázisban operáló program, gyors kereséssekkel hamar előállítja a kívánt eredményeket.</li>
</ul>
<H3>Szakterületi fogalomjegyzék</H3>
<ul>
  <li>Kurzus: Az a keret, amelyben a hallgatók meghatározott rend (előadás, gyakorlat, házi feladat, stb.) szerint gyarapítják tudásukat, és arról számot is adnak.</li>
  <li>Vizsga: Tudás számonkérése arról, hogy egy tanuló a kurzus során megtanult anyagot mennyire értette meg, és hogyan tudja alkalmazni. </li>
</ul>

<H3>Használati eset diagram</H3>
<img src="usecase.png" alt="Usecase">

<H3>Kurzuslétrehozás menete</H3>
<img src="folyamat.png" alt="Folyamat">

<H2>Tervezés</H2>

<H3>Szerepkörök</H3>
<ul>
  <li>Vendég: nem regisztrált látogató, aki csak a kezdőoldalt tudja megtekinteni, ahol csak regisztrációra/belépésre képes.</li>
  <li>Diák: lásd funkcionális követelmények</li>
  <li>Tanár: lásd funkcionális követelmények</li>
</ul>

<H3>Entitások</H3>
<ul>
  <li>User
    <ul>
      <li>Id (Integer)</li>
      <li>NeptunCode (String)</li>
      <li>Name (String)</li>
      <li>Password (String)</li>
      <li>Courses (List&lt;Course&gt;)</li>
      <li>Exams (List&lt;Exam&gt;)</li>
      <li>Role (Enum)</li>
    </ul>
  </li>
  <li>Course
    <ul>
        <li>Id (Long)</li>
        <li>Name (String)</li>
        <li>MaxLimit (Integer)</li>
        <li>Room (Room)</li>
        <li>RoomNumber (Integer)</li>
        <li>Date (String)</li>
        <li>Students (List&lt;Student&gt;)</li>
    </ul>
  </li>
  <li>Exam
    <ul>
        <li>Id (Long)</li>
        <li>Name (String)</li>
        <li>MaxLimit (Integer)</li>
        <li>Room (Room)</li>
        <li>RoomNumber (Integer)</li>
        <li>Date (String)</li>
        <li>Students (List&lt;Student&gt;)</li>
    </ul>
  </li>
  <li>Room
    <ul>
      <li>Id (Long)</li>
      <li>Name (String)</li>
      <li>MaxLimit (Integer)</li>
      <li>Occupied (Boolean)</li>
      <li>Courses (List&lt;Course&gt;)</li>
      <li>Exams (List&lt;Exam&gt;)</li>
    </ul>
  </li>
</ul>

<H3>UML Diagram</H3>
<img src="uml.png" alt="UML">

<H3>Végpontok</H3>
<ul>
  <li>GET/
    <ul>
      <li>/courses: Kurzusok megjelenítése
         <ul>
           <li>/:id : Adott id-hez tartozó kurzus megjelenítése</li>
           <li>/:id/students: Adott id-hez tartozó kurzus diákjainak megjelenítése</li>
           <li>/:id/teacher: Adott id-hez tartozó kurzus tanárának megjelenítése</li>
         </ul>
      </li>
      <li>/exams: Vizsgák megjelenítése
         <ul>
           <li>/:id : Adott id-hez tartozó vizsga megjelenítése</li>
           <li>/:id/students: Adott id-hez tartozó vizsga diákjainak megjelenítése</li>
           <li>/:id/teacher: Adott id-hez tartozó vizsga tanárának megjelenítése</li>
         </ul>
      </li>
      <li>/users: Felhasználók megjelenítése
         <ul>
           <li>/:id : Adott id-hez tartozó felhasználó megjelenítése</li>
           <li>/:id/courses: Adott id-hez tartozó felhasználó kurzusainak megjelenítése</li>
           <li>/:id/exams: Adott id-hez tartozó felhasználó vizsgáinak megjelenítése</li>
         </ul>
      </li>
      <li>/rooms: Termek megjelenítése
         <ul>
           <li>/:id : Adott id-hez tartozó terem megjelenítése</li>
           <li>/:id/courses: Adott id-vel rendelkező teremhez tartozó kurzusok megjelenítése</li>
           <li>/:id/exams: Adott id-vel rendelkező teremhez tartozó vizsgák megjelenítése</li>
         </ul>
      </li>
    </ul>
  </li>
  <li>POST/
    <ul>
      <li>/courses: Kurzus hozzáadása</li>
      <li>/exams: Vizsga hozzáadása</li>
      <li>/users: Felhasználó hozzáadása</li>
      <li>/rooms: Terem hozzáadása</li>
    </ul>
  </li>
  <li>PUT/
    <ul>
      <li>/courses/:id : Adott id-hez tartozó kurzus módosítása</li>
      <li>/exams/:id : Adott id-hez tartozó vizsga módosítása</li>
      <li>/users/:id : Adott id-hez tartozó felhasználó módosítása</li>
      <li>/rooms/:id : Adott id-hez tartozó terem módosítása</li>
    </ul>
  </li>
  <li>DELETE/
    <ul>
      <li>/courses/:id : Adott id-hez tartozó kurzus törlése</li>
      <li>/exams/:id : Adott id-hez tartozó vizsga törlése</li>
      <li>/users/:id : Adott id-hez tartozó felhasználó törlése</li>
      <li>/rooms/:id : Adott id-hez tartozó terem törlése</li>
    </ul>
  </li>
</ul>

<H3>Szekvencia diagram</H3>
<img src="szekvencia-diagramm.PNG" alt="szekvencia">

<H2>Implementáció</H2>

<H3>Felhasznált eszközök</H3>
<ul>
  <li>Github - verziókezelő</li>
  <li>NetBeans - Java fordító program</li>
  <li>Maven - project management/függőségek kezelése</li>
  <li>Spring/Springboot - keretrendszer</li>
  <li>Visual Studio Code - Lokális IDE </li>
  <li>Node.js - Javascript környezet</li>
</ul>

<H3>Könyvtárstruktúra</H3>
<ul>
  <li>controllers
    <ul>
      <li>CourseController.java</li>
      <li>ExamController.java</li>
      <li>UserController.java</li>
      <li>RoomController.java</li>
    </ul>
  </li>
  <li>entities
    <ul>
      <li>Course.java</li>
      <li>Exam.java</li>
      <li>User.java</li>
      <li>Room.java</li>
    </ul>
  </li>
  <li>repositories
    <ul>
      <li>CourseRepository.java</li>
      <li>ExamRepository.java</li>
      <li>UserRepository.java</li>
      <li>RoomRepository.java</li>
    </ul>
  </li>
  <li>security
    <ul>
        <li>AuthenticatedUser.java</li>
        <li>CustomBasicAuthenticationEntryPoint.java</li>
        <li>MyUserDetailsService.java</li>
        <li>WebSecurityConfig.java</li>
    </ul>
  </li>
  <li>NeptunApplication.java</li>
</ul>

<H2>Felhasználói dokumentáció</H2>
<H3>Telepítés</H3>
<H4>A telepítéshez szükséges:</H4>
<ul>
    <li>NodeJS és npm, ami innen letölthető: <a href="https://www.npmjs.com/get-npm/">npmjs.com/get-npm</a></li>
    <li>Internet elérés</li>
</ul>
<H4>Teleptés:</H4>
<ol>
  <li>Látogasson el a <a href="https://github.com/heymisi/alkfejl/">github.com/heymisi/alkfejl</a> oldalra.</li>
  <li>Itt kattintson a <b>"Clone and Download"</b> gombra, és azon belül kattintson a <b>"Download as Zip"</b> gombra.</li>
  <li>A letöltött állományt csomagolja ki.</li>
  <li><b>npm i</b> parancsot adjuk ki parancssorban a kicsomagolt állomány mappájában.</li>
  <li><b>npm start</b>-al elindíthatjuk a programot.</li>
</ol>
<H3>Használata</H3>
<ol>
  <li>Böngészőben a keresősávba írjuk be, hogy: <b>localhost:8080</b></li>
  <li>Regisztrálás és bejelentkezés után használhatjuk a programot.</li>
</ol>
