# 圖論筆記 (Graph Theory)：Euler, Hamiltonian, 與 Planar Graphs
逐字稿：
[[Graph Theory transcript - Euler, Hamiltonian path and cycle transcript]]
## 1. 基礎概念與圖不變量 (Graph Invariants)
*   **圖的表示法**：除了條列頂點 (Vertices) 與邊 (Edges)，也常用 **相鄰矩陣 (Adjacency Matrix)** 來有效率地表示節點間的連接關係。
*   **握手定理 (Handshaking Theorem)**：
    *   一個圖中所有頂點的度數和，等於邊數的兩倍：$\sum deg(v) = 2|E|$。
*   **圖不變量 (Graph Invariants)**：在圖同構 (Graph Isomorphism) 下保持不變的性質。
    *   $\kappa(G)$：**頂點連通度 (Vertex Connectivity)**，指最少需要移除多少個頂點才能讓圖不連通。
    *   $\lambda(G)$：**邊連通度 (Edge Connectivity)**，指最少需要移除多少條邊才能讓圖不連通。
    *   $\delta(G)$：**最小度數 (Minimum Degree)**。
    *   **定理**：對於任何圖，皆滿足 $\kappa(G) \le \lambda(G) \le \delta(G)$。

---

## 2. 尤拉路徑與尤拉環 (Euler Paths & Cycles)
源自於著名的**柯尼斯堡七橋問題 (The Seven Bridges of Königsberg, 1735, Euler)**。

*   **定義**：
    *   **Euler Path / Cycle**：一條路徑 (Path) 或環 (Cycle)，剛好走過圖中的**「每一條邊 (Edge)」確切一次**。(可以重複經過同一個頂點)。
*   **定理 (Euler Cycle 的存在性)**：
    *   一個連通的無向圖具有 Euler Cycle $\iff$ **所有頂點的度數皆為偶數 (even degree)**。
    *   *證明概念*：
        *   若存在，每次進入一個節點 $v$ 必定會從另一條邊出去，因此每個節點的度數必須成對，即 $deg(v) = 2k$ (偶數)。
        *   建構法：先找尋能走過某些邊確切一次的數個獨立 cycles（每次經過節點就會消耗偶數度數，直到回到起點），再將這些相交的 cycles 兩兩合併 (Combine pairs of cycles) 成一個單一的完整 cycle。
*   **定理 (Euler Path 的存在性)**：
    *   一個連通圖具有 Euler Path $\iff$ **剛好有 $0$ 或 $2$ 個頂點具有奇數度數 (odd degree)**。

---

## 3. 漢米爾頓路徑與漢米爾頓環 (Hamiltonian Paths & Cycles)
與 Euler 圖關注「邊」不同，漢米爾頓圖關注的是「節點」。(歷史小故事：Hamilton 曾發明 Icosian game 尋找此類環)。

*   **定義**：
    *   **Hamiltonian Path / Cycle**：一條路徑 (Path) 或環 (Cycle)，剛好走過圖中的**「每一個頂點 (Vertex)」確切一次**。
*   **複雜度**：尋找 Hamiltonian path/cycle 是一個 **NP-complete** 的困難問題，因此我們通常依賴「條件」來判斷其存在與否。

### 不存在 Hamiltonian Cycle 的條件
*   **二分圖 (Bipartite Graph)**：節點可分為 $A, B$ 兩集合，所有邊只連接著 $A$ 與 $B$。
    *   **定理**：任何具有**奇數個頂點 (odd number of vertices)** 的二分圖，**絕對沒有** Hamiltonian Cycle。(因為路徑必須在兩集合間交替，形成環必須是偶數長度)。

### 存在 Hamiltonian Cycle 的充分條件
*   **Dirac's Theorem (1952)**：
    *   對於一個 $n$ 個頂點的簡單圖 ($n \ge 3$)，若**每個節點**的度數 $deg(v) \ge \frac{n}{2}$，則該圖保證存在 Hamiltonian cycle。
*   **Ore's Theorem (1960)**：
    *   對於一個 $n$ 個頂點的簡單圖 ($n \ge 3$)，若圖中**任意兩個不相鄰節點 $u, v$**，滿足 $deg(u) + deg(v) \ge n$，則該圖保證存在 Hamiltonian cycle。
    *   *(註：滿足 Dirac 定理必滿足 Ore 定理)*
    *   **Ore's Theorem 的矛盾證法 (Proof by Contradiction)**：
        1.  假設圖 $G$ 滿足 $deg(u) + deg(v) \ge n$ 卻**沒有** Ham. cycle。
        2.  我們不斷隨機加入邊，直到形成一個極大圖 $G'$：$G'$ 本身沒有 Ham. cycle，但只要再多加一條邊就會產生 Ham. cycle。
        3.  此時 $G'$ 必定存在一條從 $u$ 到 $v$ 的 Hamiltonian path。
        4.  因為 $deg(u) + deg(v) \ge n$，根據鴿籠原理 (Pigeonhole principle)，在這條有 $n$ 個節點的路徑上，必定存在相鄰的節點，使得路徑中某點連接到 $v$ 且其前一個點連接到 $u$。
        5.  這會在 $G'$ 內部形成一個 Hamiltonian cycle，產生矛盾。故原假設錯誤。

---

## 4. 平面圖 (Planar Graphs)
*   **定義**：一個圖被稱為 Planar，若且唯若 (iff) 它可以被畫在平面上，且**沒有任何邊相交 (drawn without edge crossings)**。
*   **常見例子**：
    *   **$K_4$** (4個節點的完全圖)：**是 (Is planar)**。將其中一條對角線拉到外面畫即可避免相交。
    *   **$K_{3,3}$** (完全二分圖)：**否 (Is NOT planar)**。嘗試將節點放置於內部或外部，總會有一條邊無法避免交叉。
    *   **$K_5$** (5個節點的完全圖)：**否 (Is NOT planar)**。

---

## 5. 跨主題結合：平面圖與漢米爾頓圖
這部分的定理展示了圖論中各種不變量 (Connectivity, Planarity, Hamiltonian) 是如何相互關聯的：

*   **Tutte's Theorem (1956)**：
    *   任何 **4-連通 (4-connected, $\kappa(G) \ge 4$) 的平面圖 (planar graph)**，必定具有 Hamiltonian cycle。
*   **Thomassen's Theorem (1983)**：
    *   給定一個 4-連通的平面圖 $G$。對於圖中的**任意兩個節點 $u, v$**，必定存在一條從 $u$ 到 $v$ 的 Hamiltonian path。