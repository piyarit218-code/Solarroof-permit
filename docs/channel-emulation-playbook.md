# Channel Emulation Playbook — ช่อง "Thai Local in Phuket"

> นำระบบ "เลียนแบบช่อง 4 ขั้นตอน" (ไฟล์ CLAUDE-1.pdf) มาใช้จริง โดยวิเคราะห์จากทรานสคริปต์ของคลิปที่ดังผิดปกติ (outlier) 4 คลิปในตลาดเดียวกับเรา
> อัปเดต: 1 พ.ย. 2026 · ข้อมูลจาก vidIQ

---

## 0. ระบบนี้ดีแค่ไหน และผมปรับอะไร

**จุดดีของระบบ:**
- แยกขั้นตอนชัด: วิเคราะห์ → คิดไอเดีย → เขียนสคริปต์
- บังคับให้ติดป้าย `[VERIFY]` กับข้อมูลที่ต้องตรวจ
- เตือนว่า AI เป็นผู้ช่วย ไม่ใช่ผู้ตัดสินใจ

**จุดที่ผมปรับ:**

| ปัญหาในต้นฉบับ | การปรับ |
|---|---|
| เลียนแบบ "ช่องเดียว" ทำให้ได้สไตล์แคบเกินไป และเสี่ยงลอกจนเข้าข่าย inauthentic content | วิเคราะห์ **outlier จากหลายช่อง** ในตลาดเดียวกัน แล้วดึง **รูปแบบ** ออกมา ห้ามลอกประโยค |
| เลือก outlier ด้วยความรู้สึก | เพิ่ม **ขั้น 0:** เลือก outlier ด้วยข้อมูลจาก vidIQ (breakout score และขนาดช่อง) |
| ไม่มีขั้นวัดผล | เพิ่ม **ขั้น 5:** โพสต์ → ดูอัตราการดูจนจบ → อัปเดตไฟล์นี้ (ใช้สกิล `analytics-profit-loop`) |
| ไม่มีขั้นตรวจนโยบายก่อนโพสต์ | ให้ผ่าน `monetization-gate` ก่อนอัปโหลดทุกคลิป |

---

## 1. Outlier ที่ใช้วิเคราะห์

| # | คลิป | ช่อง | ผล | หมายเหตุ |
|---|---|---|---|---|
| O1 | RETIRED IN THAILAND REGRETS, MISTAKES? | Blue In Thailand (14.9K) | 416K วิว · **105 เท่าของปกติ** | ถ่ายดิบ ไม่ใช้ไมค์ ตอนตีห้าครึ่ง → **หัวข้อชนะคุณภาพการผลิต** |
| O2 | EMPTY THAILAND — Rent Under $180… | Golden Years Thailand (3K) | 83K · **192 เท่า** | ยาว 40 นาที ลงคลิปทุกวัน มีลักษณะช่อง AI ไม่โชว์หน้า **ให้ลอกแค่ hook ห้ามลอกรูปแบบช่อง** |
| O3 | Where I'd Retire in Thailand on a Small Pension | George Newman (19K) | 112K · 9.9 เท่า | **ขายบริการปรึกษา 1:1** ท้ายคลิป ยืนยันว่าบันไดรายได้ขั้นบริการของเราได้ผลจริง |
| O4 | My $60,000 House in Thailand | George Newman (19K) | 60K · 6 เท่า | **ติดโซลาร์ 8 แผง + แบตเตอรี่ ~฿200,000 ค่าไฟลดจาก ฿2,500–3,000 เหลือต่ำกว่า ฿700** ตรงกับความรู้โซลาร์ของคุณพอดี |

**ข้อมูลเชิงตลาดที่สำคัญที่สุด:**
- O3 เปิดคลิปว่า *"The legendary value of Phuket and Bangkok is disappearing"* และ O2 พูดว่า *"Trang is what Phuket used to be"*
- แปลว่าคนดูกำลังมองหา **"ทางเลือกที่ถูกกว่าภูเก็ต แต่อยู่ใกล้ภูเก็ต"**
- **พังงาและเขาหลักคือคำตอบนั้นพอดี** อยู่ห่างสนามบินภูเก็ตราว 1 ชั่วโมง และคุณอาศัยอยู่ที่นั่น

---

## 2. Hook Playbook — สูตรเปิดคลิป 5 สูตร

| สูตร | กลไก | ตัวอย่างจาก outlier | เทมเพลตของเรา |
|---|---|---|---|
| **H1 ตัวเลขช็อก + ข้อขัดแย้ง** | ตัวเลขชัดๆ บวกเรื่องที่ไม่น่าเป็นไปได้ ทำให้คนดูอยากรู้ | "Rent costs less than $180… and almost no expat lives there. What's wrong with these towns? Or… the expats?" | "[ราคา]. That's what [สิ่งของ] costs in [ที่]. And almost no foreigner knows." |
| **H2 มีอะไรเปลี่ยนไป + ยังมีทางออก** | สร้างความกลัวว่าจะพลาด แล้วให้ความหวัง และแสดงว่าลงพื้นที่จริง | "Something has shifted in Thailand for 2026… But the dream isn't dead. I've spent months scouting…" | "Phuket is getting expensive. But one hour north, [ข้อเท็จจริง]. I live here. Let me show you." |
| **H3 คำถามสารภาพ** | ถามคำถามที่คนดูแอบสงสัยอยู่ในใจ | "Am I regretting it? Am I missing the UK?" | ใช้ผ่านปากแขกที่สัมภาษณ์: "Do you regret moving to Phuket?" |
| **H4 วางแผนที่คลิป + ทิ้งปมไว้ตอนจบ** | บอกว่าจะตอบอะไรบ้าง และเก็บคำตอบสำคัญไว้ท้ายคลิป | "I want to answer three things… And at the end, I'll tell you whether I'd buy it again." | "Three things: price, problems, and… would I live anywhere else? Answer at the end." |
| **H5 ความลับที่คนไทยรู้** (จุดได้เปรียบเฉพาะของเรา) | ดึงความเชื่อถือจากการเป็นคนท้องถิ่น | ยังไม่มีใครในตลาดใช้สูตรนี้ | "Thais pay [X]. Foreigners pay [Y]. I'm Thai. Here's the difference." |

---

## 3. โครงสร้างสคริปต์ที่ซ้ำกันใน outlier ทั้ง 4 คลิป

```
HOOK (0:00–0:20)        สูตร H1–H5
PROMISE (0:20–0:40)     "In this video…" + ปมที่จะเฉลยตอนจบ
BODY × 3–5 ช่วง          แต่ละช่วง =
                         ① มันคืออะไร / ที่ไหน
                         ② ตัวเลขจริง (เงินบาท + USD)
                         ③ ข้อเสียแบบตรงๆ   ← ตัวสร้างความเชื่อถือ
                         ④ เหมาะกับใคร ("This is for the person who…")
                         ⑤ ประโยคเชื่อมไปช่วงถัดไป ("But if you want X, keep watching…")
VERDICT                 สรุปว่าแบบไหนเหมาะกับคนแบบไหน + เฉลยปม
CTA                     ถามคำถามให้คอมเมนต์ + ชวนใช้บริการ/ลิงก์ (O3 ขายปรึกษา 1:1)
```

**จุดที่ outlier ทุกคลิปมีเหมือนกัน:** มีช่วง "The honest bit / the catch / the downside" ในทุกช่วง เพราะคนดูวัยเกษียณกลัวโดนหลอก **ความตรงไปตรงมาจึงเป็นตัวขายที่ดีที่สุด**

---

## 4. แผนที่อารมณ์ (Emotional Escalation)

| ช่วงของคลิป | อารมณ์ที่ต้องการ | เครื่องมือ |
|---|---|---|
| Hook | อยากรู้ ตกใจ | ตัวเลข หรือข้อขัดแย้ง |
| ช่วงแรกของ Body | มั่นใจขึ้น | ตัวเลขจริง ภาพจริง |
| ช่วงกลาง | ไว้ใจ | ข้อเสียแบบตรงๆ |
| ช่วงท้าย | เห็นตัวเองในภาพ | "This is for the person who…" |
| Verdict | มีความหวังและรู้สึกเป็นส่วนหนึ่ง | "You're not a customer in an expat bubble. You're a guest in a real Thai community." (O3) |
| CTA | อยากลงมือทำ | ถามคำถามให้คอมเมนต์ / ชวนปรึกษา |

---

## 5. กลไกดึงคนดูให้อยู่ต่อ (Retention)

**ปมที่เปิดไว้ (open loop) แล้วเฉลยทีหลัง:**
- "One hides the house where a future world leader lived…" (เฉลยตอนนาทีที่ 15)
- "Something almost no YouTube video mentions… I'll tell you in the next town" (เฉลยในช่วงถัดไป)
- "At the end I'll tell you whether I'd buy it again" (เฉลยตอนท้าย)

**ประโยคดึงคนดูกลับมา (rehook) ใช้ทุก 1–2 นาที:**
- "Here's the bit people often leave out."
- "Now the honest bit."
- "Here's the bit that actually surprises people."
- "But — and this is a big but —"
- "Now, the controversial part."

**ประโยคเชื่อมระหว่างช่วง:** "But if you're willing to trade [X] for [Y], we need to head to…"

**ห้ามลอก:** O2 พูดว่า "Subscribe or YouTube will never show you this channel again" ซึ่งเป็นคำกล่าวที่ไม่จริงและเป็นการบีบคนดู ทำลายความน่าเชื่อถือ ห้ามใช้

---

## 6. ไอเดีย 20 คลิป (ขั้นที่ 3)

| # | หัวข้อ | สูตร hook | เหตุผลที่เหมาะ |
|---|---|---|---|
| 1 | **Phuket Is Getting Too Expensive. Where Thais Would Retire Instead (1 Hour Away)** | H2+H5 | ตอบเรื่องที่ O2/O3 พูดถึงโดยตรง และใช้ทำเลของคุณ |
| 2 | I Asked Phuket Expats: Do You Regret Moving Here? | H3 | หัวข้อเดียวกับ O1 ที่ได้ 105 เท่า ทำในรูปแบบสัมภาษณ์ |
| 3 | Khao Lak vs Phuket: Real Monthly Cost (Every Baht Tracked) | H1 | รูปแบบ "Every Baht" ดัง 14–26 เท่า |
| 4 | Thais Pay ฿X, Foreigners Pay ฿Y — 10 Phuket Prices Compared | H5 | จุดได้เปรียบเฉพาะคุณ |
| 5 | What ฿2 Million Buys You in Phang Nga (Real House Tour) | H1+H4 | รูปแบบเดียวกับ O4 ที่ดัง 6 เท่า |
| 6 | Solar on a Thai House: Real Cost, Real Bills, Permits Foreigners Don't Know | H1+H5 | **ความรู้โซลาร์และใบอนุญาตของคุณ** + ต่อยอดไปส่งต่อลูกค้าให้ช่างติดตั้งได้ |
| 7 | 5 Mistakes Expats Make Renting in Phuket (A Thai Explains) | H5 | เน้นความกลัวโดนหลอก |
| 8 | 70-Year-Old Retired in Khao Lak — Why He Never Went Back | H3 | รูปแบบเดียวกับ O3 |
| 9 | The Phuket Hospital Question: What Retirees Must Know | H2 | เรื่องสุขภาพเป็นความกังวลอันดับ 1 ของคนวัยเกษียณ |
| 10 | Living in Phuket on $1,500/Month — Is It Still Possible in 2027? | H2 | คนค้นหาเรื่องค่าครองชีพมาก |
| 11 | Where NOT to Live in Phuket (A Local's Honest List) | H5 | หัวข้อเชิงลบดึงคนคลิกได้ดี |
| 12 | Takua Pa Old Town: The Phang Nga Town Foreigners Drive Past | H1 | สูตร "ที่ที่คนขับผ่าน" แบบเดียวกับ O3 |
| 13 | Rainy Season in Phuket: The Truth Nobody Films | H2 | เป็นข้อเสียที่คนไม่ค่อยทำคลิป |
| 14 | Can Foreigners Buy Land in Thailand? A Thai Explains (Legally) | H5 | เกี่ยวกับอสังหาฯ ต้อง `[VERIFY]` กฎหมาย |
| 15 | I Asked Digital Nomads in Phuket How Much They Earn & Spend | H3 | คีย์เวิร์ด "digital nomad thailand" (18.9K) |
| 16 | Phuket Condo vs Phang Nga House — Same Budget, Very Different Life | H1 | ต่อไปถึงงานส่งต่อลูกค้า |
| 17 | The Electricity Bill Shock in Thailand (And How Solar Fixed It) | H1 | ข้อมูลค่าไฟจาก O1/O4 + ความรู้ของคุณ |
| 18 | 10 Thai Words That Save Expats Money at the Market | H5 | คลิปสั้น ตัดเป็น Shorts ได้ |
| 19 | Moving to Phuket With a Dog — What Nobody Tells You | H4 | ปัญหาจริงที่ O4 พูดถึง |
| 20 | My Honest Answer: Should You Retire in Phuket in 2027? | H4 | ใช้เป็นคลิปแนะนำช่อง |

---

## 7. ขั้นที่ 5 — วัดผลและอัปเดต (เพิ่มจากต้นฉบับ)

หลังลงคลิปได้ 7 วัน ให้บันทึก:
- อัตราการดูที่ 30 วินาที (เป้าหมาย 65% ขึ้นไป)
- เวลาดูเฉลี่ย (เป้าหมาย 40% ของความยาวคลิปขึ้นไป)
- CTR ของภาพปก (เป้าหมาย 4–8%)

จากนั้นอัปเดตตาราง hook ในข้อ 2: สูตรไหนชนะให้ใช้ซ้ำ สูตรไหนแพ้ให้ตัดทิ้ง
