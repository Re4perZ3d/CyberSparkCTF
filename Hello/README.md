## Challenge Description

> "Oh no, I lost my PDF! But I remember having a conversation with my friend Kakarot — can you sniff it out?"
> 

This challenge introduces participants to fundamental network forensics and password cracking. The goal is to recover an encrypted PDF shared over FTP and extract a hidden flag. Key skills include packet analysis, file extraction, AES decryption, and PDF password cracking.

---

## Solution Walkthrough

### 🧠 Step 1: Analyze the PCAP File

Open the provided `.pcap` file using **Wireshark**. Navigate to:

![Screenshot_1555.png](attachment:f595e0d0-351b-41a5-96b8-c109496f646a:Screenshot_1555.png)

- `Analyze > Follow > TCP Stream`
- Choose **Stream 0**

Inside this stream, you’ll find a message:

![Screenshot_1556.png](attachment:a3b59807-b288-4b84-b579-d44f9e8da0d3:Screenshot_1556.png)

```
Re4perZ3d: hey my friend kakarot i will send you the pdf over 21, it...s encrypted with AES-256 i used this command: openssl enc -aes-256-cbc -salt -in protected.pdf -out protected.enc -pass pass:password123

```

This provides two hints:

- The PDF was transferred over **FTP** (`port 21`)
- It was encrypted using **AES-256-CBC** with `openssl`, using password: `password123`.

---

### 📦 Step 2: Export the Encrypted File

Go to:

- `File > Export Objects > FTP`
    
    ![Screenshot_1557.png](attachment:7eb27a39-e027-453b-b60f-965368a42a24:Screenshot_1557.png)
    
- Locate and export the file named something like `protected.enc`

Save it locally.

![Screenshot_1558.png](attachment:ecab5aea-4e08-4e51-8b14-bca5fcb2c131:Screenshot_1558.png)

---

### 🔐 Step 3: Decrypt the File

Use the decryption command (as hinted in the chat):

![Screenshot_1559.png](attachment:b48ce72e-a954-4781-b97b-be9ed7b0926d:Screenshot_1559.png)

You’ll get a file named `protected.pdf`, but it’s **still password-protected**.

![Screenshot_1560.png](attachment:2a15f64e-2425-4a2a-b6be-273c230e0dd1:Screenshot_1560.png)

---

### 🔓 Step 4: Crack the PDF Password

Now, we’ll use **John the Ripper** to crack the PDF's password.

**Convert the PDF to a crackable hash:**

```bash
pdf2john protected.pdf > hash.txt

```

**Crack the hash using a wordlist (like rockyou):**

```bash
john -wordlist=/usr/share/wordlists/rockyou.txt hash.txt

```

**To see the recovered password:**

```bash
john hash.txt --show

```

Output:

```
protected.pdf:computer

```

The password is: `computer` 

![Screenshot_1561.png](attachment:dcc0a6e1-5907-46d5-b468-26949e0b6be6:Screenshot_1561.png)

---

### 📖 Step 5: Open the PDF and Retrieve the Flag

Open `protected.pdf` using the password `computer`.

![Screenshot_1562.png](attachment:75a83a1c-2503-4066-b0a1-567ad57d3781:Screenshot_1562.png)

Inside, you’ll find the flag:

```
Spark{W3lc0me_To_N3tw0rk_An4lys1s}

```

---

## Flag

```
Spark{W3lc0me_To_N3tw0rk_An4lys1s}

```

---

## Skills Learned

- 📡 **Network Traffic Analysis**: Following TCP streams to uncover conversations and hints in captured packets.
- 📁 **FTP File Extraction**: Using Wireshark to export transferred files through FTP.
- 🔐 **AES Decryption**: Understanding symmetric encryption using OpenSSL and how to decrypt with a known password.
- 🪪 **Password Cracking**: Applying tools like `pdf2john` and `john` to crack password-protected PDF files.
- 🔍 **Forensic Investigation Workflow**: Combining multiple tools and techniques to investigate, extract, decrypt, and crack protected content from network captures.
