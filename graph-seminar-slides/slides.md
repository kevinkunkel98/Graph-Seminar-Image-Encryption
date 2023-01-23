---
# try also 'default' to start simple
theme: apple-basic

image: https://images.unsplash.com/photo-1534077777481-51383522d350?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1738&q=80
layout: intro-image
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# apply any windi css classes to the current slide
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# use UnoCSS
css: unocss
---

<div class="absolute top-10">
  <span class="font-700">
    Kevin Kunkel
    <br>
    Graph-Seminar 23.01.2023
    <br>
    Prof. Dr. Stadler
  </span>
</div>

<div class="absolute bottom-30">
  <h1>Image Encryption Algorithm</h1>
  <p>Using Graph Theory and Speech Signal Key Generation</p>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# Contents

<br>

- **Introduction**
- **Proposal**
- **Encryption**
- **Decryption**
- **Key-Generation**
- **Computational Results**

<br>
<br>

---
layout: image-right
image: https://images.unsplash.com/photo-1562770584-eaf50b017307?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1902&q=80
---

# Introduction

<br>

- Developement of network technology and multimedia
- Increased transfer of images
- Need of secure transfer of images
- Many use cases for encryption (military, governments, crime, personal use)
- Developement of models combining encryption and authorization methods

---

# Arnold's Transformation

<br>

- Periodic chaotic map (an evolution function) that exhibits some sort of chaotic behavior
- Used to create randomness in the signal when applied to the signal. Here Arnold’s transform is achieved using the following matrix equation:

<br>


$$
\begin{bmatrix}x'\\y' \end{bmatrix}=\left(\begin{bmatrix}1 & 1 \\1 & 2 \end{bmatrix}\begin{bmatrix}x\\y \end{bmatrix}\right)\mod N
$$

<br>

- Where $(x',y')$ represents the new position of the pixel, whereas the $(x,y)$ the original position
- Where $N$ indicates size or order of an image matrix

<br>

---


# Arnold's Transformation: Example

<br>
<br>


<img border="rounded" src="/assets/pic1.png">


<center>

**Figure 1:** Examples of an image subjected to Arnold’s Transform, (a) Original image, (b) Image
obtained after 1st iteration, (c) Image obtained after 2nd iteration, (d) Image obtained after 384th
iteration

</center>


---
layout: image-right
image: /assets/propose.png
---
# Proposal

<br>
<br>
<br>
<br>
<br>

**Figure 2:** shows a Diagram of the steps of the proposed algorithm.
---

# Scanning-Methodology

<br>

- A combined system of compression, coding, and hiding proposed by Bourbakis in 1986 (SCAN-Language)
- The word " SCAN " refers to the different methods of scanning
a two-dimensional image. The SCAN language can produce a(mxm)!
- SCAN can be stored in adjecancy matrices
- Let $G$ be a graph with vertices set and edge set $E(G)={ϱ_1, ϱ_2, ϱ_3…, ϱ_m}$

---

# SCAN-Process

<br>

Scans             |  Partitions
:-------------------------:|:-------------------------:
![](/assets/grid.png)  |  ![](/assets/grid2.png) 


<center> 

**Figure 3:** shows how images are being scanned and partitioned.

</center>

---

# Encryption-Algorithm

<font size="1">

<br>

- **Input:** Original color image (256x265px), speech signal, scan pattern
- **Output:** Cipher color image
- **Step 1:** Input the color image
- **Step 2:** Read the color image and then split it in to into R, G, and B levels. For each input matrix
- level (R, G and B), divide the color image into 16 sub-blocks of size 64×64 pixels.
- **Step 3:** Get the starting a modified Spiral S scan to read the values from each sub-block and save them at new block of same size (64×64) Then collect all blocks at new scrambling image of size
(64×64). Show Figure 4. and Table 1.
- **Step 4:** Divide each level (R, G and B) into 64 sub-block of length 32*32 pixel at each level do the following steps:
  - Convert each block to the vector of length 1024 value.
  - Divide the vector into 4 vectors each of which have 256 value.
  - Perform XOR operation between the four vectors and secret key vectors. Form the keys matrix
  selected two keys of length 512 then divide each key into two keys of length 256.
  - Perform XOR between the vector and the first part of secret key, the result of this operation has
been xored again to the second part of secret key.
  - Convert back the four vectors into one vector then convert it back to sub block of 32×32 pixels.
  - Use Arnold transform for each sub-block.
- **Step 5:** Combine the 64 sub-blocks back into an encrypted color image of size 256×256.
- **Step 6:** Store the cipher color image.

</font>  

---

# Decryption-Algorithm

<font size="1">

<br>

- **Input:** Cipher image, described color image
- **Output:** Color image
- **Step 1:** Input the cipher color image of sizes 256×256px
- **Step 2:** Divide each level (R, G and B) into 64 sub-block of length 32×32 pixels at each level do the
following steps:
  - Use Arnold transform for each sub-block.
  - Convert each block to the vector of length 1024 values.
  - Divide the vector into 4 vectors each of which have 256 values.
  - Perform XOR between the vector and the first part of secret key, the result of this operation has been xored again to the second part of secret key
  - Perform XOR operation between the four vectors and secret key vectors. Form the keys matrix selected two keys of length 512 then divide each key into two keys of length 256.
  - Convert back the four vectors into one vector then convert it back to sub block of 32×32
pixels.
(64×64). Show Figure 4. and Table 1.
- **Step 3:** Combine the 64 sub-blocks back into a decrypted color image of size 256×256 pixels.
- **Step 4:** Read the decrypted color image then divids it in to into R, G, and B levels. For each input
matrix level (R, G and B), divide the decrypted color image into 8 sub-blocks of size 64×64 pixels.
- **Step 5:** Get the starting a modified Spiral S scan to return the values from each sub-block to the real
position and save them at new block of same size (64×64 pixels). Then collect all blocks at new
descrambling image of size (64×64 pixels). 
- **Step 6:** Combine the 16 sub-blocks back into a descrambled color image of size 256×256 pixels
- ***Step 7:** Store the decrypted color image.

</font>  

---

# Key-Generation (Using Graph Theory)

- encryption and decryption use same key
- verbal signal of length 10 ms is divided into blocks of size(256) values
- blocks converted into square matrices (16x16) where matrix is defined as connected graph
- connected graph generates the keys by using the adjecency matrix (1 for existing interconnect 0 for none)
- adjacency matrix multiplied by lower triangular $m$ to then again be converted to an adjacency matrix
- using the Mod function to reduce resulting values to be identified between 0-255 (pixel values)
- Mod funciton generates keys that extract values from matrix (to maintain a randomness)
- create a key vector with 512 length

---


# Example images

<br>
<br>

<img border="rounded" src="/assets/examples.png">

<center> 

**Figure 4:** shows example images used for computation.

</center>


---

# Example Encryption

Original             |  Encrypted
:-------------------------:|:-------------------------:
![](/assets/or.png)  |  ![](/assets/cr.png) 

---

# Computation Results (Original)

| | **Diagonal Correlation** | **Vertical Correlation** | **Horizontal Correlation** |
| --- | ------- | -------- | -------- |
| Baboon | 0.9437 | 0.9635 | 0.9694 |
| Lena | 0.9212 | 0.9720 | 0.9460 |
| Pepper | 0.9478 | 0.9773 | 0.9715 |
| Mona Liza | 0.9866 | 0.9927 | 0.9932 |
| Rose | 0.9636 | 0.9868 | 0.9736 |
| Child | 0.9567 | 0.9741 | 0.9727 |
| Barbara | 0.9040 | 0.9259 | 0.8829 |


---

# Computation Results (Cipher)

| | **Diagonal Correlation** | **Vertical Correlation** | **Horizontal Correlation** |
| --- | ------- | -------- | -------- |
| Baboon | 0.0048 | -0.0013 | -0.00033 |
| Lena | -0.0030 | 0.0006  | 0.0066 | 
| Pepper | 0.0009 | -0.0046 | -0.0010 |
| Mona Liza | 0.0065 | -0.0030 | -0.0095 |
| Rose | -0.0002 | -0.0051 | -0.0039  |
| Child | 0.0026 | 0.0001 | -0.0030 |
| Barbara | 0.0021 | 0.0054 | -0.0016 |

---

# Entropy Measures of Proposed Algorithm

<br>
<br>

| **Color Image** | **Entropy Original Image** | **Entropy Encrypted Image** |
| --- | ------- | -------- |
| Baboon | 7.6128 | 7.9988 |
| Lena | 7.7599 | 7.9987 |
| Pepper | 7.7749 | 7.9987 |
| Mona Liza | 7.3808 | 7.9981 |

---

# Conclusion

- exchange of image data through open channels is dangerous
- reqirement of additional security
- paper presents encryption algorithm for color images
- depends on passing an audio signal in several stages and stores keys in a database
- looking at data shows that the proposed algorithm offers strong security against brute force attacks

---

# Paper
<br>
<br>
<br>
<br>
<br>

I. Q. Abduljaleel et al 2021, An Image of Encryption Algorithm Using Graph
Theory and Speech Signal Key Generation, J. Phys.: Conf. Ser. 1804 012005
