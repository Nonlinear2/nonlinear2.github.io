People writing chess engines love acronyms. There are way too many, so i've written a small glossary of chess programming acronyms.

--  **general chess**:

[`SF`](https://stockfishchess.org/): Stockfish
[`LC0`](https://lczero.org/): Leela Chess Zero
`FEN`: Forsyth-Edwards Notation
`EPD`: Extended Position Description
`PGN`: Portable Game Notation
`FRC`/`DFRC`: (Double) Fisher Random Chess
`TC`: Time Control / [TalkChess](https://talkchess.com/)
`STM`: Side-To-Move
`50MR`: 50 Move Rule
[`CCC`/`CCCC`](https://www.chess.com/computer-chess-championship): (Chess.<area>com) Computer Chess Championship
[`TCEC`](https://tcec-chess.com/): Top Chess Engine Championship
[`CCRL`](https://computerchess.org.uk/ccrl/404/): Computer Chess Rating Lists
[`CPW`](https://www.chessprogramming.org/Main_Page): Chess Programming Wiki
[`OB`](https://github.com/AndyGrant/OpenBench): OpenBench

--  **general engines**:

`SSS`: Small Sample Size
[`UCI`](https://www.wbec-ridderkerk.nl/html/UCIProtocol.html): Universal Chess Interface
`SPRT`: Sequential Probability Ratio Test
`LLR`: Log Likelihood Ratio
`SPSA`: Simultaneous Perturbation Stochastic Approximation
`NPS`: Nodes Per Second
`STC / LTC / VLTC`: Short Time Control / Long Time Control / Very Long Time Control
`WDL`: Win/Draw/Loss
`SB`: SuperBatch
[`EAS`](https://www.sp-cc.de/eas-ratinglist.htm): Engine Aggressiveness Score
`GHI`: Graph History Interaction
`TB` / `EGTB`: (EndGame) TableBase:
- `DTM`: Depth To Mate
- `DTZ`: Depth To Zeroing

--  **search**:

`TM`: Time Management
`PV`: Principal Variation
`TT`: Transposition Table
`ID`/`IID`: (Internal) Iterative Deepening
`QS`: Quiescence Search
`SMP`: Symmetric Multiprocessing
`MCTS`: Monte Carlo Tree Search
`PUCT`: Predictor Upper Confidence Tree

--  **heuristics**:

`IIR`: Internal Iterative Reductions
`RFP`: Reverse Futility Pruning
`FP / FFP`: (Forward) Futility Pruning
`NMP`: Null Move Pruning
`LMP`: Late Move Pruning
`LMR`: Late Move Reduction
`PVS`: Principal Variation Search
`ZWS`: Zero Window Search
`SE`: Singular Extensions
`SEE`: Static Exchange Evaluation
`HP`: History Pruning

--  **move ordering**:

`MVV-LVA` : Most Valuable Victim, Least Valuable Aggressor
`HH`: History Heuristic
`CMH`: Counter Move History
`PCM`: Prior CounterMove

--  **evaluation**:

`NNUE`: Efficiently Updatable Neural Network
`HM`: Horizontal mirroring
`HCE`: Hand Crafted Evaluation
`PST / PSQT`: Piece Square Table
`BAE`: Big Array Eval
`RFB`: Rook Forward Bonus
`KS`: King Safety