# WIRESHARK PACKET ANALYSIS
## INTRODUCTION
This report presents the findings from an in-depth analysis of a provided packet capture (PCAP) file
using Wireshark, a widely used network protocol analysis tool. The objective of this assessment was
to inspect network traffic, extract transferred files, and identify any hidden or suspicious content.
To streamline the analysis, HTTP traffic was filtered using the http display filter, allowing focused
inspection of relevant communications.
![Wireshark Screenshot](https://github.com/CYBER-PIKIN/Wireshark-Packet-Analysis/blob/main/Images%20Screenshot/Screenshot%202026-05-07%20215921.png?raw=1)

## Analysis and Findings
## Sub-Task 1: Extraction of Network Images
Objective:
Identify and extract image files observed in network traffic.
Findings:
Two images—anz-logo.jpg and bank-card.jpg—were identified within the captured traffic.
Methodology:
* Followed the relevant TCP streams in Wireshark
* Identified JPEG file signatures using hexadecimal headers and footers (FFD8 / FFE9)
* Extracted the hex data and reconstructed the images using a hex editor (HxD)
* Saved the reconstructed files in .jpg format
Result:
Both images were successfully extracted and reconstructed.
Anz-logo :
Bank-Card :
## Sub-Task 2: Hidden Content in Images (ANZ1.jpg & ANZ2.jpg)
Objective:
Analyze images for hidden or embedded data.
Findings:
Two images (ANZ1.jpg and ANZ2.jpg) were extracted using the same reconstruction process as
above.
Upon further inspection of ANZ1.jpg, a hidden message was discovered within the ASCII data:
“You've found a hidden message in this file! Include it in your write up.”
Conclusion:
The image contained concealed data, indicating potential use of steganography or embedded
metadata.
ANZ1 : ANZ2 :
## Sub-Task 3: Suspicious Document Analysis
Objective:
Retrieve and analyze the contents of a suspicious file:
how-to-commit-crimes.docx
Methodology:
* Followed the corresponding TCP stream
* Examined the ASCII representation of the file contents
Findings:
The document content was successfully recovered directly from the packet stream and reviewed.
## Sub-Task 4: PDF Document Extraction
Objective:
Extract and review accessed PDF files:
 ANZ_Document.pdf
 ANZ_Document2.pdf
 evil.pdf
Methodology:
 Identified file boundaries using appropriate file signatures 20/0A
 Extracted hex data from TCP streams
 Reconstructed files using a hex editor
Result:
All three PDF documents were successfully extracted and analyzed. Solution
ANZ_Document : ANZ_Document2 :
Evil.pdf :
## Sub-Task 5: Hidden Message File
Objective:
Analyze the file hiddenmessage2.txt
Findings:
 The file was initially misleading, as it appeared to be a text file
 Upon inspection, it was identified as a JFIF (JPEG) file
Methodology:
 Extracted and reconstructed using JPEG headers
 Converted into .jpg format
Result:
The file revealed an image (hiddenmessage2.jpg) containing the intended hidden content.
Hiddenmessage2.jpg :
## Sub-Task 6: ATM Image Traffic Analysis
Objective:
Analyze the file atm-image.jpg and identify anomalies.
Findings:
 The traffic associated with this image showed irregularities
 Further inspection shows that the traffic contains more than one embedded image
Result:
The image was successfully extracted, confirming unusual characteristics in its transmission.
atm-images.jpg :
## Sub-Task 7: Broken PNG Image Recovery
Objective:
Recover and analyze broken.png
Findings:
 The file contained a Base64-encoded PNG image
 Identified by the signature iVBOR, commonly associated with Base64-encoded PNG files
Methodology:
 Decoded the Base64 content using an external decoding tool, base64.guru was used for the
conversion
 Converted the output into a valid .png image
Result:
The image was successfully reconstructed and viewed.
## Sub-Task 8: Secure PDF Extraction
Objective:
Access and extract contents of securepdf.pdf
Findings & Methodology:
 Identified embedded content within the file
 Discovered a hidden archive structure (ZIP format) using signature analysis (504B / 0506)
 Extracted the archive and located a file named rawpdf.pdf

 Identified the password “secure” within the traffic analysis
 Successfully decrypted Using the password which is “secure” that was gotten during the
analysis stage and accessed the document rawpdf.pdf
Result:
The protected PDF file was extracted and its contents reviewed.
Rawpdf.pdf :
Conclusion
The analysis of the packet capture revealed multiple instances of file transfers, hidden data, and
obfuscation techniques within network traffic. Several files were deliberately disguised or encoded
to evade detection, including:
 Embedded messages within images
 Misleading file extensions
 Base64 encoding
 Password-protected and archived content
This exercise highlights the importance of deep packet inspection and forensic analysis techniques
in identifying hidden threats and uncovering concealed information within network communications.
Key Takeaways
 File signatures are critical for identifying true file types
 TCP stream analysis is essential for reconstructing transferred data
 Attackers often use encoding, encryption, and steganography to hide data
 Tools like Wireshark and hex editors are invaluable in network forensics
