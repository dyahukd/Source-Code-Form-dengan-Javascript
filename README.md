# Source-Code-Form-dengan-Javascript
Berikut adalah source code untuk membuat Form Registrasi Mahasiswa dengan Javascript dan HTML.
```
<html>
<head>
  <meta charset="UTF-8">
  <title>Learning Javascript</title>
  <style>
    body {
      font-family: Palatino, Georgia;
      background-color: #fff5f7;
    }
    .form-container {
      border: 2px solid pink;   
      padding: 20px;
      border-radius: 10px;
      width: 400px;
      background-color: #fff;   
      box-shadow: 0px 4px 12px rgba(243, 133, 151, 0.3);
    }
    h2 {
      font-size: 32px;
      color: rgb(243, 133, 151); 
      margin-top: 0; 
      text-align: center;
    }
    label {
      font-size: 20px;
      display: block;
      margin-top: 10px;
    }
    input[type="text"] {
      outline: none;
      border: 2px solid pink;
      padding: 6px;
      border-radius: 6px;
      font-size: 18px;
      width: 95%;
      margin-bottom: 15px;
      transition: 0.3s;
    }
    input[type="text"]:focus {
      border-color: rgb(243, 133, 151);
      box-shadow: 0 0 5px rgba(243, 133, 151, 0.6);
    }
    button {
      padding: 8px 15px;
      font-size: 16px;
      border-radius: 6px;
      border: none;
      background-color: rgb(243, 133, 151);
      color: white;
      cursor: pointer;
      transition: 0.3s;
    }
    button:hover {
      background-color: pink;
      box-shadow: 0 3px 6px rgba(243, 133, 151, 0.4);
    }
    #rekomendasi {
      border:1px solid #ccc;
      max-width:95%;
      font-size: 16px;
      margin-top: 2px;
      border-radius: 5px;
      background: #fff;
    }
    #rekomendasi div {
      padding: 5px;
      cursor: pointer;
    }
    #rekomendasi div:hover {
      background: #ffe4ec;
    }
  </style>
  <script>
    let daftarnama = ["Andi Yusri", "Ahmad Pradipta", "Anisa Alya", "Budi Pramana", "Bagas Aji", "Citra Mahira", "Chesilya Azzahra", "Dyah Utami", "Dewi Ayu"];

    function tampilkanrekomendasi(form) {
      let input = form.nama.value.toLowerCase();
      let rekomendasi = daftarnama.filter(nama => nama.toLowerCase().startsWith(input));

      let kotak = document.getElementById("rekomendasi");
      kotak.innerHTML = "";

      if (input === "") return;

      rekomendasi.forEach(nama => {
        let item = document.createElement("div");
        item.textContent = nama;
        item.onclick = () => {
          form.nama.value = nama;
          kotak.innerHTML = "";
        };
        kotak.appendChild(item);
      });
    }

    function formvalidation(form) {
      let nama = form.nama.value;
      let nrp = form.nrp.value;
      let matkul = form.matkul.value;
      let dosen = form.dosen.value;

      if (nama === "") {
        alert("Nama tidak boleh kosong!");
        return false;
      }
      if (nrp === "") {
        alert("NRP tidak boleh kosong!");
        return false;
      }
      if (matkul === "") {
        alert("Mata kuliah tidak boleh kosong!");
        return false;
      }
      if (dosen === "") {
        alert("Dosen tidak boleh kosong!");
        return false;
      }

      alert("Registrasi berhasil!");
      return true;
    }
  </script>
</head>
<body>
  <div class="form-container">
    <h2>Form Registrasi Mahasiswa</h2>
    <form onsubmit="return formvalidation(this)">
      <label for="nama">Nama Mahasiswa:</label>
      <input type="text" name="nama" autocomplete="off" onkeyup="tampilkanrekomendasi(this.form)">
      <div id="rekomendasi"></div>

      <label for="nrp">NRP:</label>
      <input type="text" name="nrp">

      <label for="matkul">Mata Kuliah:</label>
      <input type="text" name="matkul">

      <label for="dosen">Dosen:</label>
      <input type="text" name="dosen">

      <button type="submit">Daftar</button>
    </form>
  </div>
</body>
</html>
```
