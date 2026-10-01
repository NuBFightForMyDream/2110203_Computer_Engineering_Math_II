# CEMII Lab — 2110203 Visualizers

เปิด `index.html` ในเบราว์เซอร์ → หน้ารวมที่แบ่งตาม part ของวิชา กดเลือก lecture แล้วหน้านั้นจะเปิดในหน้าเดียวกัน

## โครงสร้าง

```
Visualizer Web/
├── index.html                          ← หน้ารวม (เมนู + รายการตาม part)
├── Signal Part I/
│   ├── convolution-lab.html            ← Lecture 02 Convolution
│   ├── fourier-ct.html                 ← Lecture 03 Fourier (เวลาต่อเนื่อง)
│   ├── fourier-dt.html                 ← Lecture 04 DTFS / DTFT / DFT / FFT
│   ├── sampling-filtering.html         ← Lecture 05 Sampling & Filtering
│   └── quantum-fourier.html            ← เสริม: Quantum Fourier Transform (ต่อจาก Lecture 04)
└── Optimization/                       ← ยังว่าง

../Midterm Signals/index.html           ← เฉลย Midterm Quiz 2 (ลิงก์จาก Signal Part I ด้วย path)
```

แต่ละไฟล์ `.html` เป็นไฟล์เดียวจบ (CSS + JS อยู่ในตัว) เปิดเดี่ยว ๆ ก็ได้ กราฟทุกอันคำนวณสดจากสูตร ไม่ได้ฝังรูปไว้

## เพิ่ม lecture ใหม่

1. วางไฟล์ `.html` ของ lecture ไว้ในโฟลเดอร์ของ part นั้น เช่น `Optimization/simplex.html`
2. เปิด `index.html` แล้วเพิ่ม object ใน `lectures` ของ part นั้นใน `PARTS`:

```js
{ id: 'simplex', no: '07', title: 'Simplex', th: 'ซิมเพล็กซ์', file: 'simplex.html',
  desc: 'คำอธิบายสั้น ๆ', tags: ['แท็ก 1', 'แท็ก 2'] }
```

3. part ใหม่ = เพิ่ม object ใน `PARTS` (`folder` คือชื่อโฟลเดอร์, `short` คือชื่อสั้นบนแถบเมนู)

ลิงก์ออนไลน์ (Claude artifact) ใช้หน้าเดียวกันนี้ แต่รวมไฟล์ lecture ไว้ข้างในแล้ว จึงเปิดได้จากลิงก์เดียว

## ที่มาของตัวเลขในแต่ละหน้า

| หน้า | โจทย์/ค่าที่ตรวจกับสไลด์แล้ว |
| --- | --- |
| Convolution | Ex 2.1 `y = {1,5,5,−5,−6,4,1,−2}` · Ex 2.2 `y[2] = 0.5278` · Ex 2.5 `y(−0.8) = 1.2` · Ex 2.6 `y(1.2) = 0.251` |
| Fourier CT | คลื่นสี่เหลี่ยม `a₁ = −j2/π` · Ex 3.2 `a₀ = 1, a₁ = 1 − 0.5j, a₂ = 0.5∠π/4` |
| Fourier DT | `x = {1,2,0,−1}` → `X[k] = {2, 1−3j, 0, 1+3j}` · circular conv. `{−6, 6, 7, −5}` |
| Quantum Fourier | วงจร H + R<sub>k</sub> + swap ตรงกับสูตร `y_k = (1/√N) Σ x_n e^{j2πkn/N}` ทุก input (q = 1–6, ต่างกัน < 1e−14) · 15 = 3 × 5 ด้วย a = 7, r = 4 |
| Sampling | `f = 13 Hz, fs = 10 Hz → fp = 3 Hz` · เสียง 5 kHz → `ωs = 62832 rad/s, T = 0.1 ms` |
