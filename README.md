# Literature Matrix: Thai ASAG + Feedback (QE)

Oct 27, 2026 · @chutipontrir

## ภาพรวม

เก็บไว้ 31 ฉบับใน 8 หมวด ตัดออก 4 ฉบับ ตัวเลขทุกตัวมาจากไฟล์ PDF ที่แนบมา (อ่านบทคัดย่อ ระเบียบวิธี และผลลัพธ์) ยกเว้นรายการที่ติด \[ใหม่\] ไฟล์ 01–04 ที่ส่งซ้ำ (ฉบับมีโน้ตลายมือ) ไม่นับซ้ำ

**วิธีอ่าน:** รหัส A1, B3 … ใช้อ้างในบท literature · **\[add-on\]** = 15 ฉบับที่เพิ่มรอบนี้ · **\[ใหม่\]** = พบเพิ่มจาก references ของ RUBRA (ยังไม่มีไฟล์ ตรวจจาก arXiv)

| หมวด | ใช้ตอบอะไรในงานวิจัย | จำนวน |
| --- | --- | --- |
| A. ASAG ภาษาไทย | สถานะงานไทย, จุดอ่อนเชิงวิธีวิทยา | 6 |
| B. วิธี/สถาปัตยกรรม ASAG สากล | การออกแบบระบบ (LLM, rubric, RAG, XAI) | 5 |
| C. Feedback ใน ASAG | taxonomy และการวัดคุณภาพ feedback | 4 |
| D. ภาพ/ลายมือ | input PDF/PNG ของระบบ | 4 |
| E. Reliability ของ LLM grader | ความตรง, bias, human-in-the-loop | 2 |
| F. ผลต่อการเรียนรู้และการสอน | edu impact, การออกแบบการทดลองระยะยาว | 6 |
| G. Survey | วางกรอบ field | 2 |
| H. Thai NLP พื้นหลัง | บริบทภาษาไทย | 2 |
| ตัดออก | — | 4 |

## A. ASAG ภาษาไทย

งานไทยขยับจาก TF-IDF ไป ML แล้วไป LLM แต่การวัดผลยังอ่อน มีเพียง A6 ที่ใช้ psychometrics (ICC, G-theory)

| # | งาน | วิธี / ข้อมูล | ผลที่รายงาน | จุดอ่อน / ใช้ในงานเรา |
| --- | --- | --- | --- | --- |
| A1 | Aungkaseraneekul & Jaruskulchai (ม.เกษตรฯ) | TF-IDF + cosine + K-NN แบ่ง 5 ระดับ; 55 คน 5 ข้อ วิชา OOP | accuracy 76.73–92.73% | งานยุคแรก ข้อมูลเล็ก |
| A2 | Wangwiwattana & Tongvivat, ICETM 2022 | keyword matching, sentence vector ranking, TF-IDF + K-Means | keyword เหมาะกับคำตอบตายตัว, clustering เหมาะกับคำตอบหลากหลาย | ไม่มี agreement กับครู; เป็นเครื่องมือกึ่งอัตโนมัติ |
| A3 | Wongsara, Homjun & Ketui (มทร.ล้านนา น่าน) | TF-IDF + cosine; 170 คำตอบ, ผู้ใช้ 20 คน | ความพึงพอใจ x̄ = 4.05 (S.D. 0.81) | ไม่ได้วัดความตรงของคะแนน |
| A4 | Rattanimit & Nomponkrang, iEECON 2025 | PyThaiNLP + NB / DT / SVM; 120 คน คำถามคำสั่ง Python | SVM accuracy 85.33%; ผู้เชี่ยวชาญพึงพอใจ 4.05 | รายงานเฉพาะ accuracy |
| A5 | Thongyoo, Utanon & Utanon, วารสาร IT & นวัตกรรม 2569 (2026) \[add-on\] | PyThaiNLP + Bag-of-Words (CountVectorizer) + logistic regression; 1,000 คำตอบ rubric 11 ระดับ; แบ่ง 80:20 | accuracy 90.00%; precision 0.87–0.94; recall 0.83–0.94; F1 0.86–0.93 | ไม่มี kappa/QWK; อ้างว่าลดเวลาตรวจแต่ไม่ได้วัด |
| A6 | **Kondinchi & Tuksino, 2025 (มข.)** | o3-mini (คัดจาก GPT-4o-mini, GPT-4o) + analytic rubric; ม.3 300 คน; จับใจความ สรุปความ ย่อความ; ระบบ ASSWT | r = .496–.819; ICC = .815–.945; G-theory ρ²δ .26 → .62, ρ²Δ .17 → .51 | **ใกล้งานเราที่สุด** มีข้อเสนอแนะทันที แต่ไม่ได้ประเมินคุณภาพ feedback และไม่ได้ติดตามผลระยะยาว |

## B. วิธี/สถาปัตยกรรม ASAG สากล

แนวโน้มคือ rubric-guided + retrieval + human-in-the-loop แต่ไม่มีงานไหนในหมวดนี้วัดผล feedback ต่อผู้เรียน

| # | งาน | วิธี / ข้อมูล | ผลที่รายงาน | จุดอ่อน / ใช้ในงานเรา |
| --- | --- | --- | --- | --- |
| B1 | Minnegalieva & Ziyatdinova, SCM 2025 (03) | cosine บน BERT/LLM + binary classifier; ค่าน้ำหนักคำจาก SVM + TF-IDF; ทดลอง ChatGPT ตรวจ; คำตอบ 1–3 ประโยค วิชา computer graphics | ทุกวิธียังตรวจผิดได้ ต้องใช้ร่วมกัน; คำถามกำกวมทำให้แม่นยำลดลง | หลักฐานว่า “ครูต้องปรับคำถาม” เป็น feedback ถึงครูได้ |
| B2 | Minnegalieva et al., Inforino 2026 (04) | cosine คัดกรอง → LIME หาคำสำคัญ → ตรวจซ้ำเฉพาะช่วง cosine 0.3–0.7 | 20 คำตอบที่เคยตรวจผิด กลับมาตรงกับผู้เชี่ยวชาญ | ฐานของ “ทำไมได้/เสียคะแนน” แต่ตัวอย่างเล็ก ไม่มี agreement statistic |
| B3 | **Haldar, Sengupta & Das, CIACON 2025 — RUBRA** | agentic 5 agent: สร้าง rubric จากเฉลย, RAG จากตำรา (FAISS + all-MiniLM-L6-v2), ให้คะแนนถ่วงน้ำหนักด้วย cosine ราย rubric item, feedback, orchestrator; SciEntsBank 10,804 คำตอบ 5 คลาส | accuracy 71.5%, macro-F1 69.8% (GPT-3.5 zero-shot 69.2% / 65.1%); partially correct 68.9%; ตัด RAG → accuracy ลด 5.2 จุดตาม Table III (เนื้อความในเปเปอร์เขียน 7.4% ตัวเลขไม่ตรงกัน) | ไม่บอก split (unseen answers/questions/domains); ตัด feedback agent แล้ว accuracy ลด 1.1 จุด (เนื้อความเขียน 1.5%) ทั้งที่ feedback สร้างหลังให้คะแนน ไม่มีคำอธิบาย; ไม่มีคนประเมิน feedback; MiniLM เป็นอังกฤษ **หยิบใช้:** misconception lookup table, HITL flag, feedback อ้างหน้าตำรา |
| B4 | Karjus et al., 2026 (Estonia, arXiv 2601.16314) | LLM + statistical NLP ตรวจเรียงความระดับชาติ 2 cohort ตาม rubric หลักสูตร | ผลอยู่ในช่วงเดียวกับคนตรวจ; ทดสอบ bias และ prompt injection | อ้างว่าภาษาเล็กทำระดับชาติได้; subscore → feedback รายบุคคล |
| B5 | Fateen, Wang & Mine, 2024 — Beyond Scores \[ใหม่\] | RAG แบบ modular ให้คะแนน + feedback; ชุด SAF; Mistral-7B, Llama3-70B (zero/few-shot) | accuracy +9% บนคำถามที่ไม่เคยเห็น เทียบ fine-tuned baseline | **แบบอย่างการประเมิน feedback:** ครู 5 คน Likert (accuracy, clarity) + BLEU/ROUGE/BERTScore |

## C. Feedback ใน ASAG

feedback ใน ASAG ส่วนใหญ่ยังเป็นแค่ evaluative (บอกคะแนน) ชุดข้อมูลที่มี feedback อธิบายเหตุผลมีน้อย และไม่มีภาษาไทย

| # | งาน | วิธี / ข้อมูล | ผลที่รายงาน | จุดอ่อน / ใช้ในงานเรา |
| --- | --- | --- | --- | --- |
| C1 | Manso Vázquez et al., EDUCON 2026 (01) | ทบทวน 87 งาน ASAG ใน 2 ปี คัด 35 งาน STEM; จำแนก feedback ถึงนักเรียน: evaluative, descriptive, directive, facilitative, affective และแยก feedback ถึงครู | evaluative มากที่สุด รองลงมา descriptive แบบอื่นพบน้อย | work-in-progress 3 หน้า; **ใช้เป็น taxonomy ของ RQ2** |
| C2 | Aggarwal, Sil, Raman & Bhattacharyya — EngSAF (arXiv 2407.12818v2, 2025) \[add-on\] | 5,814 คำตอบ 119 คำถาม 25 วิชาวิศวกรรม; ป้าย correct/partial/incorrect + feedback สังเคราะห์ด้วย Gemini (LASFG) แล้วให้คนตรวจ | Mistral-7B fine-tuned: 75.4% (unseen answers), 58.7% (unseen questions); ใช้จริงในสอบปลายภาค 92.5%; feedback correctness และ emotional impact > 4.5/5 | feedback สังเคราะห์ ไม่ใช่ครูเขียน; ตกหนักบนคำถามใหม่; **ยืม rubric ประเมิน feedback (FC/EI) ได้** |
| C3 | Filighera, Parihar, Ochs, Steuer & Meuser, ACL 2022 — SAF \[add-on\] | 4,519 submissions คำถามภาษาอังกฤษและเยอรมัน; ทุกคำตอบมี score, label, elaborated feedback จาก annotator; เปิด dataset + rubric (MIT) | baseline T5 / mT5 สำหรับให้คะแนนพร้อมสร้าง feedback | **ต้นแบบการสร้าง Thai feedback dataset**; ชี้เรื่อง emotional effect ของ feedback ต้องคุมใน annotation guideline |
| C4 | Imran & Bulathwela (UCL), 2026 — Correct Answer Trap \[add-on\] | 20,964 คำตอบคณิต (Eedi) พร้อมคำอธิบาย; test 3,702 คำตอบ มี hidden misconception 61 ราย (1.6%) | fine-tuned classifier จับได้ 57%; reasoning model จับได้ 84% แต่ false alarm มากกว่าจริง \~8:1 | เสนอ rubric แยก answer mark กับ method mark และ detect–verify–escalate; **เตือนว่า feedback ที่ดูแค่คำตอบถูก/ผิด จะตอกย้ำ misconception** |

## D. รับคำตอบจากภาพ/ลายมือ

pipeline ภาพ→คะแนนทำได้แล้วในภาษาสเปน สโลวีเนีย และคณิตศาสตร์ แต่ทุกงานยังต้องส่งต่อให้คนตรวจ 17–70% และลายมือไทยคือจุดอ่อนที่สุดของ VLM

| # | งาน | วิธี / ข้อมูล | ผลที่รายงาน | จุดอ่อน / ใช้ในงานเรา |
| --- | --- | --- | --- | --- |
| D1 | Yarovenko-Kuzminykh et al., EDUNINE 2026 (02) | HTR ด้วย LLM สำหรับคำตอบสั้นภาษาสเปน เทียบ 8 โมเดล | GPT-5 98.53%, Gemini-2.5-flash 97.68%, Qwen2.5-VL-7B 93.52%, Google Vision API 65.10%, LLaVA-13B 27.65% | ข้อมูลผู้วิจัยสร้างเอง ไม่ใช่ข้อสอบจริง; โมดูลตรวจคะแนนยังไม่เสร็จ |
| D2 | Nonesung et al. (SCB 10X), 2025 — ThaiOCRBench | benchmark VLM ภาษาไทย 2,808 ตัวอย่าง 13 ประเภทงาน, zero-shot | handwritten extraction และ fine-grained text recognition ตกมากที่สุดใน open-source; proprietary (เช่น Gemini 2.5 Pro) นำ | **หลักฐานตรงว่าขั้น OCR ลายมือไทยเป็นจุดเสี่ยง**; พบ hallucination, language bias |
| D3 | Kortemeyer, Caspar & Horica (ETH), arXiv 2510.05162v2, 2025 \[add-on\] | GPT-5 ตรวจงานเขียนมือแคลคูลัส ตาม rubric เดียวกับ TA; 342 ฉบับ; filter = partial-credit threshold + IRT 2PL risk | AI vs TA: R² ≈ 0.85, slope ≈ 0.92, offset ≈ 1.12; กรองเข้มได้ความแม่นระดับคน แต่เหลือ \~70% ให้คนตรวจ | ผู้เขียนสรุปเองว่า R² 0.85 พอสำหรับ feedback low-stakes ไม่พอสำหรับ high-stakes; **ยืมแนวคิด IRT-based routing ได้** |
| D4 | Perš, Muhovič, Košir & Murovec (Ljubljana), arXiv 2601.00730, 2026 \[add-on\] | A4 ลายมือภาษาสโลวีเนีย (มี circuit schematic); เฉลยลายมือของอาจารย์→สรุปเป็นข้อความ; presence check, ensemble grader, supervisor, template ตรวจแบบ deterministic; GPT-5.2 / Gemini-3 Pro | mean absolute difference ≈ 8 คะแนนจากอาจารย์, bias ต่ำ; ส่งคนตรวจ ≈ 17% (Dmax = 40); ตัดเฉลยออก→ให้คะแนนเกิน | ทดสอบ quiz held-out เดียว ผู้ตรวจคนเดียว; **ต้นแบบ pipeline ภาพของระบบเรา** |

## E. ความน่าเชื่อถือของ LLM grader

LLM สอดคล้องกับตัวเองสูง แต่อาจไม่ตรงกับคนตรวจ โดยเฉพาะข้อเชิงวิเคราะห์ จึงต้องรายงาน agreement หลายตัวและมี human-in-the-loop (A6 ใช้ G-theory เป็นตัวอย่างฝั่งไทย)

| # | งาน | วิธี / ข้อมูล | ผลที่รายงาน | จุดอ่อน / ใช้ในงานเรา |
| --- | --- | --- | --- | --- |
| E1 | Jade & Yartsev, arXiv 2505.04645, 2025 \[add-on\] | ChatGPT-4o ตรวจ 557 คำตอบ (215 คน) คอร์ส mechanical ventilation ระดับบัณฑิต; 5 sessions; mixed-effects, ICC, kappa, Kendall’s W, Bland-Altman | bias −1.34/10; ICC1 = 0.086; kappa = −0.079; ระหว่าง session สอดคล้องกัน (G = 0.87); > 60% ต่างจากคนเกินเกณฑ์ | ข้อ evaluative/analytic แย่ที่สุด ข้อ checklist ดีกว่า; ผู้ตรวจคนเดียว; **ใช้เป็นเหตุผลให้ rubric แตกเป็น checkpoint** |
| E2 | Hardy (Stanford), arXiv 2603.04820v2, 2026 — Autoscoring Anticlimax \[add-on\] | meta-regression 890 ค่า QWK จากงาน LLM short-answer scoring (ASAP-SAS, งานเขียนเด็ก K-12) + การทดลอง wording/tokenization | decoder-only แย่กว่า encoder เฉลี่ย 0.37 QWK; ความยากสำหรับคนไม่ทำนายความยากสำหรับ LLM; ตัวอย่างงานเดียวกันได้คะแนน 1 vs 0 ตามเชื้อชาติที่ระบุ | **เหตุผลที่ต้องเทียบ baseline แบบ encoder (เช่น WangchanBERTa) คู่กับ LLM** และตรวจ bias |

## F. ผลของ feedback ต่อการเรียนรู้และการสอน

feedback ที่ให้ข้อมูลครบได้ผลสูง (d = 0.99) แต่ไม่มี RCT ไหนที่วัดผลการเรียนรู้จาก feedback ของระบบ ASAG โดยตรง นี่คือ gap หลักของงานเรา

| # | งาน | วิธี / ข้อมูล | ผลที่รายงาน | จุดอ่อน / ใช้ในงานเรา |
| --- | --- | --- | --- | --- |
| F1 | Wisniewski, Zierer & Hattie, Front. Psychol. 2020 \[add-on\] | meta-analysis 435 งาน, k = 994, N > 61,000; random-effects | d = 0.48 (ก่อนตัด outlier 0.55); high-information feedback d = 0.99, corrective 0.46, reinforcement/punishment 0.24; ผลต่อ cognitive/motor สูงกว่า motivational/behavioral | heterogeneity สูง feedback ไม่ใช่ treatment เดียว; **เหตุผลที่ต้องบอก “ทำไมผิด” ไม่ใช่แค่คะแนน** |
| F2 | Fleckenstein, Liebenow & Meyer, Front. Artif. Intell. 2023 \[add-on\] | meta-analysis เครื่องมือ AWE; 20 งาน, k = 84, N = 2,828; three-level model | g = 0.55 ต่อ writing performance; moderator ต่างกันแต่ไม่มี subgroup ไหนมีนัยสำคัญ | เป็นงานเขียน ไม่ใช่ short answer; ใช้ค่า g เป็นฐานคำนวณ power/sample size ได้ |
| F3 | Heinrich, Baily, Chen, DeOliveira, Park & Wang, PLOS One 2025 \[add-on\] | RCT 4 วิชา รัฐศาสตร์ 2023–24; 271 คน 26 tests 3,080 คำตอบ (88% ตรวจด้วย AI); GPT-4 + เกณฑ์ + ตัวอย่างที่อาจารย์ตรวจ \~10 ข้อ | grade discrimination ไม่ต่างจากคน; ขอ regrade น้อยกว่า; helpfulness ต่างเล็กน้อยและต่างตามวิชา | **ไม่ได้วัดผลการเรียนรู้** (สุ่มระดับคำตอบ ทุกคนได้ AI feedback); ใช้เป็นตัวอย่างการออกแบบ RCT ในห้องจริง; เปิด data/code บน OSF |
| F4 | Cao, Zhao, Schunn, McLaughlin, Lin & Koedinger, arXiv 2604.07469v2, 2026 \[add-on\] | RCT ออนไลน์ 199 คน: sequenced AI feedback (กำลังใจ + hint ก่อนเฉลย) vs เฉลยพร้อมคำอธิบายทันที; mediation analysis | sequenced ได้ post-test ต่ำกว่า (adjusted mean ≈ 10.4 vs 11.2) แม้รู้สึก encouragement สูงกว่า; เส้นทางบวกจาก encouragement ถูกหักล้างด้วยพฤติกรรมส่งซ้ำ ≥ 3 ครั้ง | ผู้เรียนออนไลน์ ไม่ใช่ห้องเรียน; **เตือนว่ารูปแบบ feedback อาจทำให้ผลแย่ลง ต้องวัด engagement + gaming** |
| F5 | Demszky & Liu, EdWorkingPaper 23-759, 2023 \[add-on\] | RCT 414 mentor (Polygence); เครื่องมือ NLP ให้ feedback ผู้สอนหลังทุก session (uptake, talk time, questioning) | 84% เปิดหน้า feedback; uptake +9% (บทคัดย่อเขียน 10%), questioning +6%, talk time −5%; นักเรียน optimism สูงขึ้น | ไม่มีผลต่อผลงานสุดท้ายของนักเรียน; **ต้นแบบ “feedback ถึงครู” และการวัด uptake** |
| F6 | Dong, Tang & Wang, Computers & Education: AI 2025 | meta-analysis 29 งาน N = 2,657 (PRISMA) | AI ต่อผลสัมฤทธิ์ g = 0.924 | รวม AI ทุกประเภท; ใช้เป็นภาพกว้างเท่านั้น |

## G–H. Survey, Thai NLP พื้นหลัง และรายการที่ตัดออก

survey ทั้งสองฉบับใช้วางกรอบ field ส่วน Thai NLP ใช้อ้าง 1–2 ประโยค

| # | งาน | สาระสำคัญ | ใช้ในงานเรา |
| --- | --- | --- | --- |
| G1 | Haller, Aldea, Seifert & Strisciuglio, arXiv 2204.03503, 2022 \[add-on\] | ทบทวน ASAG ยุค deep learning แบ่งเป็น word embeddings, sequential models, attention; พบว่า representation ที่เรียนรู้อย่างเดียวไม่ชนะ ผลดีสุดมาจากการรวม hand-engineered features กับ transformer | ประวัติ field ก่อนยุค LLM; สนับการใช้ rubric/keyword ร่วมกับโมเดล |
| G2 | Nkoyo, Ijezue, Amjad, Amjad, Butt & Castañeda-Garza, BEA 2025 \[add-on\] | ทบทวน 30 งาน LLM grading 6 สาขา; ปัญหา: ความไม่สม่ำเสมอ, ต้องมี human oversight; เรียกร้อง classroom validation เพื่อดูผลระยะยาวต่อการเรียนรู้ | **อ้างตรง ๆ ว่า field เรียกร้องงานแบบที่เราทำ** |
| H1 | Arreerard, Mander & Piao, LREC 2022 | survey Thai NLP: งาน upstream (tokenisation) ก้าวหน้า แต่ downstream ด้าน semantic ยังมีน้อย | บริบทว่าทำไม Thai ASAG ยังตามหลัง |
| H2 | Limkonchotiwat et al., 2025 (arXiv 2504.05898) | benchmark ภาษาถิ่นเหนือ/อีสาน/ใต้ 5 งาน: LLM ตกชัดเทียบภาษากลาง มีแค่ GPT-4o และ Gemini ที่พอใช้ได้ | ประเด็น fairness ถ้านักเรียนตอบด้วยภาษาถิ่น |

**ตัดออก (4 ฉบับ)**

- ThaiCoref (Trakuekul et al.) — coreference resolution ไม่ตอบ RQ
- Udomcharoenchaikit, วิทยานิพนธ์ จุฬาฯ 2020 — เทคโนโลยีแกน Thai NLP ไม่ตอบ RQ (อ่านเฉพาะหน้าปก)
- Tulasi & Ahamed, ICONSTEM 2024 — กว้าง ไม่เกี่ยวกับ ASAG หลักฐานอ่อน → ใช้ F1, F2, F6 แทน
- Khalkho & Singh, ICAIQSA 2024 — แบบสอบถามอาจารย์ 54 คน → ใช้ F1, F2, F6 แทน

## Gap และการผูกกับ RQ

gap หลักคือยังไม่มีใครปิดลูป ASAG → feedback → ผลการเรียนรู้และการสอนที่เปลี่ยนไป ทั้งในไทยและในชุดที่ทบทวน (ยืนยันได้แค่ว่า “ไม่พบ” ยังไม่ได้ทำ systematic search)

| Gap | หลักฐาน | RQ ที่ตอบ |
| --- | --- | --- |
| 1. Thai ASAG วัดผลอ่อน: ส่วนใหญ่รายงาน accuracy หรือความพึงพอใจ ไม่พบ QWK หรือ dataset เปิด | A1–A5 vs A6; E2 | RQ1 agreement กับครู (QWK, ICC, G-theory) |
| 2. feedback หยุดที่คะแนน ไม่มี diagnostic feedback ภาษาไทย และ feedback ถึงครูแทบไม่มี | C1, C2, C3, B3 (ไม่ประเมิน feedback), B5 | RQ2 คุณภาพ feedback ตาม taxonomy C1 + F1 ให้ครูประเมิน (แบบ B5/C2) |
| 3. ไม่มีงานติดตามผลระยะยาวเมื่อครู-นักเรียนทำตาม feedback ของ ASAG | F3 ไม่วัดการเรียนรู้; F4 ชี้ว่ารูปแบบอาจให้ผลลบ; G2 เรียกร้องงานในห้องเรียน | RQ3 ผลต่อการเรียนรู้ (มีกลุ่มเปรียบเทียบ, delayed post-test, วัด uptake) |
| 4. feedback ถึงครูเปลี่ยนการสอนได้จริง แต่ไม่เคยทำกับผล ASAG | F5, B1 | RQ4 ครูปรับการสอนอย่างไร และส่งผลอย่างไร |
| 5. pipeline ลายมือไทย → คะแนน ยังไม่มีใครทดสอบ และไม่มีใครวัดว่า error OCR ส่งผลต่อคะแนน/feedback เท่าไร | D1–D4 | RQ1 แยก typed vs image |
| 6. reliability/fairness ของ LLM ในภาษาไทย และเกณฑ์ส่งต่อคนตรวจ | E1, E2, D3, D4, C4, H2 | RQ1 + การออกแบบ HITL threshold |

**ข้อควรระวังตอน QE:** RQ3 ต้องมีกลุ่มเปรียบเทียบ (quasi-experiment หรือ crossover ระหว่างห้อง) มิฉะนั้นสรุปเชิงเหตุผลไม่ได้ และควรใช้ g = 0.55 (F2) หรือ d = 0.48 (F1) เป็นฐานคำนวณขนาดตัวอย่าง

## บรรณานุกรม

เรียงตามรหัส ลิงก์เฉพาะฉบับที่เปิดหน้าต้นทางแล้ว ฉบับอื่นอ้างจากไฟล์ PDF

- A1 Aungkaseraneekul, S., & Jaruskulchai, C. Automated Thai-Language Essay Scoring using K-NN. มหาวิทยาลัยเกษตรศาสตร์.
- A2 Wangwiwattana, C., & Tongvivat, Y. (2022). Semi-Automatic Short-Answer Grading Tools for Thai Language using NLP. ICETM 2022. doi:10.1145/3582580.3582600
- A3 Wongsara, R., Homjun, K., & Ketui, N. การพัฒนาระบบตรวจข้อสอบอัตนัยภาษาไทยบนพื้นฐานการวัดค่าความคล้ายคลึง. มทร.ล้านนา น่าน.
- A4 Rattanimit, W., & Nomponkrang, T. (2025). NLP for Subjective Exam Grading in Programming Explanations in Thai Language. iEECON 2025. doi:10.1109/iEECON64081.2025.10987594
- A5 Thongyoo, T., Utanon, W., & Utanon, E. (2026). [Development of an Automated Scoring System for Thai Short-Answer Responses](https://so03.tci-thaijo.org/index.php/oarit/article/view/301475). วารสารเทคโนโลยีสารสนเทศและนวัตกรรม, 25(1).
- A6 Kondinchi, C., & Tuksino, P. (2025). The Development of an Automated Scoring System for Assessing Writing Test in the Thai Language Subject at the Lower Secondary Level. Journal of Inclusive and Innovative Education, 9(3).
- B1 Minnegalieva, C., & Ziyatdinova, S. (2025). Automated Analysis of Short Answers Using Text Similarity Vectorization. SCM 2025. doi:10.1109/SCM66446.2025.11060299
- B2 Minnegalieva, C., et al. (2026). Using Explainable AI Methods to Improve Knowledge Assessment Results. Inforino 2026. doi:10.1109/Inforino68543.2026.11556666
- B3 Haldar, S., Sengupta, S., & Das, A. K. (2025). RUBRA: An Agentic AI System for ASAG Using LLMs and RAG. CIACON 2025. doi:10.1109/CIACON65473.2025.11189329
- B4 Karjus, A., et al. (2026). Machine-Assisted Grading of Nationwide School-Leaving Essay Exams with LLMs and Statistical NLP. arXiv:2601.16314
- B5 Fateen, M., Wang, B., & Mine, T. (2024). [Beyond Scores: A Modular RAG-Based System for ASAS with Feedback](https://arxiv.org/html/2409.20042v2). arXiv:2409.20042
- C1 Manso Vázquez, M., et al. (2026). Feedback in Automatic Short Answer Grading and Scoring Systems. EDUCON 2026. doi:10.1109/EDUCON67543.2026.11574413
- C2 Aggarwal, D., Sil, P., Raman, B., & Bhattacharyya, P. (2025). [“I understand why I got this grade”: ASAG with Feedback](https://arxiv.org/pdf/2407.12818). arXiv:2407.12818v2
- C3 Filighera, A., Parihar, S. S., Ochs, S., Steuer, T., & Meuser, T. (2022). [Your Answer is Incorrect… Would you like to know why?](https://www.kom.tu-darmstadt.de/papers/FPS+22-1.pdf) ACL 2022.
- C4 Imran, M., & Bulathwela, S. (2026). [The Correct Answer Trap](https://arxiv.org/pdf/2606.23205). arXiv:2606.23205
- D1 Yarovenko-Kuzminykh, N., et al. (2026). First steps towards automated grading of handwritten short answers with LLMs. EDUNINE 2026. doi:10.1109/EDUNINE62390.2026.11547041
- D2 Nonesung, S., et al. (2025). ThaiOCRBench. arXiv:2511.04479
- D3 Kortemeyer, G., Caspar, A., & Horica, D. (2025). [AI Grading Assistance for Handwritten Components of a Calculus Exam](https://arxiv.org/html/2510.05162v2). arXiv:2510.05162v2
- D4 Perš, J., Muhovič, J., Košir, A., & Murovec, B. (2026). [Grading Handwritten Engineering Exams with Multimodal LLMs](https://arxiv.org/html/2601.00730v1). arXiv:2601.00730
- E1 Jade, T., & Yartsev, A. (2025). [ChatGPT for automated grading of short answer questions in mechanical ventilation](https://arxiv.org/abs/2505.04645v1). arXiv:2505.04645
- E2 Hardy, M. (2026). [Autoscoring Anticlimax](https://arxiv.org/html/2603.04820v2). arXiv:2603.04820v2
- F1 Wisniewski, B., Zierer, K., & Hattie, J. (2020). [The Power of Feedback Revisited](https://www.frontiersin.org/articles/10.3389/fpsyg.2019.03087/full). Frontiers in Psychology, 10:3087.
- F2 Fleckenstein, J., Liebenow, L. W., & Meyer, J. (2023). [Automated feedback and writing: a multi-level meta-analysis](https://www.leibniz-ipn.de/en/research/publications/automated-feedback-and-writing). Frontiers in AI, 6:1162454.
- F3 Heinrich, T., et al. (2025). [AI-assisted grading and personalized feedback in large political science classes](https://pmc.ncbi.nlm.nih.gov/articles/PMC12364334). PLOS One, 20(8): e0328041.
- F4 Cao, J., et al. (2026). [Assessing the Impact and Underlying Pathways of Sequenced AI Feedback on Student Learning](https://arxiv.org/pdf/2604.07469). arXiv:2604.07469v2
- F5 Demszky, D., & Liu, J. (2023). [M-Powering Teachers](https://edworkingpapers.com/sites/default/files/ai23-759.pdf). EdWorkingPaper 23-759.
- F6 Dong, L., Tang, X., & Wang, X. (2025). Examining the effect of AI in relation to students’ academic achievement: A meta-analysis. Computers and Education: AI, 8, 100400.
- G1 Haller, S., Aldea, A., Seifert, C., & Strisciuglio, N. (2022). [Survey on ASAG with Deep Learning](https://arxiv.org/pdf/2204.03503). arXiv:2204.03503
- G2 Nkoyo, F. E. T.-A., et al. (2025). [Advances in Auto-Grading with LLMs: A Cross-Disciplinary Survey](https://aclanthology.org/2025.bea-1.35.pdf). BEA 2025, pp. 477–498.
- H1 Arreerard, R., Mander, S., & Piao, S. (2022). Survey on Thai NLP Language Resources and Tools. LREC 2022, pp. 6495–6505.
- H2 Limkonchotiwat, P., et al. (2025). Assessing Thai Dialect Performance in LLMs. arXiv:2504.05898
