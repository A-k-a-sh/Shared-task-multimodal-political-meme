Tamil images: 803, Malayalam images: 500

Total samples: 1303
Tamil: 803, Malayalam: 500

=== TABLE 1: Dataset Statistics ===
 Language  Total  Support  Troll  Person  Party Intersection
    Tamil    803      112    691     633    170            -
Malayalam    500       23    477     327    120           53

LaTeX format:
\begin{tabular}{lrrrrrl}
\toprule
Language & Total & Support & Troll & Person & Party & Intersection \\
\midrule
Tamil & 803 & 112 & 691 & 633 & 170 & - \\
Malayalam & 500 & 23 & 477 & 327 & 120 & 53 \\
\bottomrule
\end{tabular}

CLIP embeddings shape: (1303, 768)

Face features shape: (1303, 2)


Loading logos from: /kaggle/input/datasets/dfvdrgvd/shared-task-political-party-logos/logos
Checking for subdirectories (one per party)...
  → AAP: 3 logos
  → AIADMK: 2 logos
  → BJP: 
/usr/local/lib/python3.12/dist-packages/PIL/Image.py:981: UserWarning: Palette images with Transparency expressed in bytes should be converted to RGBA images
  warnings.warn(
3 logos
  → CPI: 2 logos
  → CPI(M): 3 logos
  → DMK: 3 logos
  → INC: 3 logos
  → IUML: 4 logos
  → LDF: 1 logos
  → NTK: 2 logos
  → PMK: 4 logos

============================================================
✅ Loaded logos: 30
   Skipped logos: 0

   Final logo embedding shape: (30, 768)
   Unique parties: 11
   Parties: [np.str_('AAP'), np.str_('AIADMK'), np.str_('BJP'), np.str_('CPI'), np.str_('CPI(M)'), np.str_('DMK'), np.str_('INC'), np.str_('IUML'), np.str_('LDF'), np.str_('NTK'), np.str_('PMK')]


============================================================
Computing logo features for all memes...
============================================================
Logo Features: 100%|██████████| 1303/1303 [00:00<00:00, 59123.27it/s]

✅ Logo features shape: (1303, 3)
   Features: [max_sim, top2_gap, hits]
   Sample values (first meme): [ 0.4548307   0.02516532 21.        ]
   Min values: [1.9605191e-01 1.3709068e-06 0.0000000e+00]
   Max values: [ 0.63937366  0.07800156 26.        ]
   Mean values: [3.8726515e-01 1.2621125e-02 1.7056791e+01]
============================================================


============================================================
FINAL FEATURE MATRIX (CLIP + Face + Logo)
============================================================
CLIP embeddings:  768d
  Face features:    2d  (num_faces, max_face_area)
  Logo features:    3d  (max_sim, top2_gap, hits)
───────────────────────────
          TOTAL:  773d
        Samples: 1303
============================================================
✅✅✅ PERFECT MATCH! Shape (1303, 773)
     This matches your official submission!
     Ready to run CV evaluation and get correct results!
============================================================


✅ CLIP features ready for ablation: (1303, 768)


⚠️  This will take approximately 90 minutes to complete (~30 min per feature set)
    Running 5-fold CV for 3 feature combinations × 2 languages × 2 tasks = 60 models

================================================================================
ABLATION STUDY: Testing Feature Combinations
================================================================================

────────────────────────────────────────────────────────────────────────────────
Testing: CLIP only (768d)
────────────────────────────────────────────────────────────────────────────────
       Tamil: Stance=0.8292  Target=0.5705  Avg=0.6999
   Malayalam: Stance=0.6372  Target=0.5181  Avg=0.5777

────────────────────────────────────────────────────────────────────────────────
Testing: CLIP + Face (770d)
────────────────────────────────────────────────────────────────────────────────
       Tamil: Stance=0.8243  Target=0.5860  Avg=0.7051
   Malayalam: Stance=0.6248  Target=0.5010  Avg=0.5629

────────────────────────────────────────────────────────────────────────────────
Testing: CLIP + Face + Logo (773d)
────────────────────────────────────────────────────────────────────────────────

       Tamil: Stance=0.8138  Target=0.5733  Avg=0.6936


   Malayalam: Stance=0.6488  Target=0.4898  Avg=0.5693

================================================================================
ABLATION STUDY RESULTS TABLE
================================================================================

Formatted Table:
         `                     Average F1           Stance F1           Target F1          
Language                       Malayalam     Tamil Malayalam     Tamil Malayalam     Tamil
Features           Dimensions                                                             
CLIP + Face        770          0.562894  0.705140  0.624820  0.824280  0.500968  0.586001
CLIP + Face + Logo 773          0.569271  0.693562  0.648769  0.813848  0.489774  0.573277
CLIP only          768          0.577678  0.699875  0.637216  0.829230  0.518141  0.570520

================================================================================
TABLE FOR PAPER (Copy this format):
================================================================================

CLIP only (768d):
  Tamil:     Stance=0.8292  Target=0.5705  Avg=0.6999
  Malayalam: Stance=0.6372  Target=0.5181  Avg=0.5777

CLIP + Face (770d):
  Tamil:     Stance=0.8243  Target=0.5860  Avg=0.7051
  Malayalam: Stance=0.6248  Target=0.5010  Avg=0.5629

CLIP + Face + Logo (773d):
  Tamil:     Stance=0.8138  Target=0.5733  Avg=0.6936
  Malayalam: Stance=0.6488  Target=0.4898  Avg=0.5693

================================================================================
IMPROVEMENT ANALYSIS:
================================================================================

Tamil:
  Face adds:  Stance +-0.0049  Target +0.0155
  Logo adds:  Stance +-0.0104  Target +-0.0127
  Total gain: Stance +-0.0154  Target +0.0028

Malayalam:
  Face adds:  Stance +-0.0124  Target +-0.0172
  Logo adds:  Stance +0.0239  Target +-0.0112
  Total gain: Stance +0.0116  Target +-0.0284


=== TABLE 2: Cross-Validation Results (5-fold) ===
 Language Level 1 (Stance) F1 Level 2 (Target) F1 Average F1
    Tamil              0.8138              0.5742     0.6940
Malayalam              0.6454              0.4897     0.5675

LaTeX format:
\begin{tabular}{llll}
\toprule
Language & Level 1 (Stance) F1 & Level 2 (Target) F1 & Average F1 \\
\midrule
Tamil & 0.8138 & 0.5742 & 0.6940 \\
Malayalam & 0.6454 & 0.4897 & 0.5675 \\
\bottomrule
\end{tabular}


=== TABLE 3: Official Test Results ===
 Language         Split  Level 1 F1  Level 2 F1  Avg F1  Rank
Malayalam Official Test      0.9638      0.6222  0.7930     1
    Tamil Official Test      0.9271      0.6060  0.7666     6

LaTeX format:
\begin{tabular}{llrrrr}
\toprule
Language & Split & Level 1 F1 & Level 2 F1 & Avg F1 & Rank \\
\midrule
Malayalam & Official Test & 0.963800 & 0.622200 & 0.793000 & 1 \\
Tamil & Official Test & 0.927100 & 0.606000 & 0.766600 & 6 \\
\bottomrule
\end{tabular}

============================================================
TAMIL - Per-Class Performance
============================================================
STANCE:
              precision    recall  f1-score   support

     SUPPORT     0.6508    0.7321    0.6891       112
       TROLL     0.9557    0.9363    0.9459       691

    accuracy                         0.9078       803
   macro avg     0.8032    0.8342    0.8175       803
weighted avg     0.9132    0.9078    0.9101       803


TARGET:
              precision    recall  f1-score   support

       PARTY     0.3193    0.4471    0.3725       170
      PERSON     0.8336    0.7441    0.7863       633

    accuracy                         0.6812       803
   macro avg     0.5765    0.5956    0.5794       803
weighted avg     0.7247    0.6812    0.6987       803

============================================================
MALAYALAM - Per-Class Performance
============================================================
STANCE:
              precision    recall  f1-score   support

     SUPPORT     0.2778    0.4348    0.3390        23
       TROLL     0.9720    0.9455    0.9586       477

    accuracy                         0.9220       500
   macro avg     0.6249    0.6901    0.6488       500
weighted avg     0.9400    0.9220    0.9301       500
TARGET:
              precision    recall  f1-score   support

INTERSECTION     0.2083    0.1887    0.1980        53
       PARTY     0.5364    0.4917    0.5130       120
      PERSON     0.7427    0.7768    0.7593       327

    accuracy                         0.6460       500
   macro avg     0.4958    0.4857    0.4901       500
weighted avg     0.6365    0.6460    0.6407       500

