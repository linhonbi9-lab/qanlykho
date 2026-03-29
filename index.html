<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Quản lý mét dư</title>

  <script src="https://unpkg.com/html5-qrcode"></script>

  <style>
    body { font-family: Arial; padding: 10px; }
    input, select, button { width: 100%; padding: 10px; margin: 5px 0; }
    table { width: 100%; border-collapse: collapse; margin-top: 10px; }
    th, td { border: 1px solid #ccc; padding: 6px; text-align: center; }

    .done { background: red; color: white; }
    .du { background: orange; }
    .het { background: lightgreen; }
  </style>
</head>

<body>

<h3>📦 Quản lý mét dư</h3>

<select id="px">
  <option value="">-- Chọn phân xưởng --</option>
  <option value="may1">May 1</option>
  <option value="may2">May 2</option>
  <option value="may3">May 3</option>
  <option value="inep">In ép</option>
</select>

<input id="barcode" placeholder="Barcode">
<input id="mavattu" placeholder="Mã vật tư">

<input id="tong" type="number" placeholder="Tổng mét (cuộn)">
<input id="yeucau" type="number" placeholder="Yêu cầu cấp">
<input id="metdu" type="number" placeholder="Mét dư" readonly>

<button onclick="addData()">➕ Lưu</button>

<input id="search" placeholder="🔍 Tìm">

<table>
<thead>
<tr>
<th>Barcode</th>
<th>Mã</th>
<th>PX</th>
<th>Tổng</th>
<th>YC</th>
<th>Dư</th>
<th>Trạng thái</th>
<th>Ngày</th>
<th>Xuất</th>
<th>Xoá</th>
</tr>
</thead>
<tbody id="table"></tbody>
</table>

<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/12.11.0/firebase-app.js";
import { getFirestore, collection, addDoc, onSnapshot, deleteDoc, doc, updateDoc } from "https://www.gstatic.com/firebasejs/12.11.0/firebase-firestore.js";

const app = initializeApp({
  apiKey: "AIza...",
  authDomain: "khodulieu-68b4e.firebaseapp.com",
  projectId: "khodulieu-68b4e"
});
const db = getFirestore(app);

let data = [];

const pxInput = document.getElementById("px");
const barcodeInput = document.getElementById("barcode");
const mavattuInput = document.getElementById("mavattu");
const tongInput = document.getElementById("tong");
const yeucauInput = document.getElementById("yeucau");
const metduInput = document.getElementById("metdu");
const searchInput = document.getElementById("search");


// 🔥 TỰ TÍNH DƯ
function tinhDu() {
  const tong = Number(tongInput.value);
  const yc = Number(yeucauInput.value);

  if (!tong || !yc) return;

  metduInput.value = tong - yc;
}

tongInput.addEventListener("input", tinhDu);
yeucauInput.addEventListener("input", tinhDu);


// 🔥 LƯU
window.addData = async function () {
  const tong = Number(tongInput.value);
  const yc = Number(yeucauInput.value);
  const du = Number(metduInput.value);

  if (tong && yc && tong < yc) {
    alert("❌ Sai: Tổng < yêu cầu");
    return;
  }

  let status = "Cấp đúng";
  if (tong === yc) status = "Cấp hết";
  if (tong > yc) status = "Cấp dư";

  await addDoc(collection(db, "metdu"), {
    barcode: barcodeInput.value,
    mavattu: mavattuInput.value,
    tong,
    yeucau: yc,
    metdu: du,
    phanxuong: pxInput.value,
    status,
    done: false,
    time: new Date().toISOString(),
    ngay: new Date().toLocaleDateString("vi-VN")
  });

  barcodeInput.value = "";
  mavattuInput.value = "";
  tongInput.value = "";
  yeucauInput.value = "";
  metduInput.value = "";
};


// 🔥 HIỂN THỊ
function render() {
  const table = document.getElementById("table");
  table.innerHTML = "";

  let filtered = data;

  const key = searchInput.value.toLowerCase();

  if (key) {
    filtered = filtered.filter(i =>
      (i.mavattu || "").toLowerCase().includes(key) ||
      (i.barcode || "").toLowerCase().includes(key)
    );
  }

  filtered.forEach((item, i) => {

    let cls = "";
    if (item.status === "Cấp dư") cls = "du";
    if (item.status === "Cấp hết") cls = "het";

    table.innerHTML += `
      <tr class="${cls}">
        <td>${item.barcode || ""}</td>
        <td>${item.mavattu || ""}</td>
        <td>${item.phanxuong || ""}</td>
        <td>${item.tong || ""}</td>
        <td>${item.yeucau || ""}</td>
        <td>${item.metdu || ""}</td>
        <td>${item.status || ""}</td>
        <td>${item.ngay || ""}</td>
        <td><button onclick="toggle(${i})">${item.done ? "✅" : "📦"}</button></td>
        <td><button onclick="del(${i})">X</button></td>
      </tr>
    `;
  });
}


window.toggle = async function (i) {
  await updateDoc(doc(db, "metdu", data[i].id), {
    done: !data[i].done
  });
};

window.del = async function (i) {
  if (!confirm("Xoá?")) return;
  await deleteDoc(doc(db, "metdu", data[i].id));
};

searchInput.addEventListener("input", render);

onSnapshot(collection(db, "metdu"), (snap) => {
  data = snap.docs.map(d => ({ id: d.id, ...d.data() }));
  render();
});
</script>

</body>
</html>
