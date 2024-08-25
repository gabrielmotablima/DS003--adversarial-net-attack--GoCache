# 🎉 DS003 - Adversarial Network Attack (GoCache)
The current project is a basic approach of data analysis and statistics modeling to get business insights and propose strategies to fight an adversarial network server attack.

![image](https://github.com/gabrielmotablima/DS003--adversarial-net-attack--GoCache/assets/31813682/f69244a2-e263-414b-81f4-71d2018bf0cd)

---

### Objectives:
  - Analize the server requests to discover anomalous activies.
  - Bring up insights about the server activities and possible adversarial attacks.
  - Propose actions to mitigate possible attacks.

### Results:
  - Estimated a upper threshold to specify a period as an adversarial attack period.
  - Bring up the understanding of the characteristics of an attack period.
  - Proposed for the next steps to mitigate future attacks.

# 🎩 Step 1. Business problem understanding

Data dictionary:
- hora: The timestamp when the request was made (e.g. 2024-05-15 15:59:56 UTC).
- ip: The IP address (possibly anonymized or hashed) from which the request originated (e.g. 3.16.1a6931d1b...).
- metodo: The HTTP method used for the request (GET, POST, HEAD, XCGFULLBAN, and OPTIONS).
- protocolo: The protocol used for the request (HTTP/2.0, HTTP/1.1, and HTTP/1.0).
- hostname: The hostname or server name where the request was directed (codes starting with cab, ea6, and 145).
- uri: The Uniform Resource Identifier (URI) requested by the client (e.g. /f276ac316f69...).
- querstring: The query string part of the URL, which typically contains parameters for the request.
- status_code: The HTTP status code returned by the server (e.g., 200).
- useragent: The User-Agent string provided by the client (e.g. Mozilla/5.0).
- tamanho_request: The size of the HTTP request sent by the client.
- tamanho_resposta: The size of the HTTP response returned by the server.
- organizacao: The organization associated with the IP address (e.g. AS16509 AMAZON-02).
- pais: The country where the request originated, based on the IP address (e.g. US).
- cidade: The city where the request originated, based on the IP address (e.g. Columbus).
- cookie_sessao: The session cookie value (e.g. 1e0a93baad5dd480...).
- fingerprint1: First part of a set of fingerprinting values used to uniquely identify a client (e.g. b2bcc0e205d8ec...).
- fingerprint2: Second part of the fingerprinting values (e.g. 844de68e6dea18...).
- fingerprint3: Third part of the fingerprinting values (e.g. 16af3145e3eee5...).

# 📊 Step 2. Data analysis focused in anomaly detection

## Attacks interval

![image](https://github.com/user-attachments/assets/dc372d4b-f833-4bb6-abfb-da209ffa1a31)

## All requests (left) vs Attack requests (right)
<p align="center">
<img src='https://github.com/user-attachments/assets/e7f93e1e-6c03-45e5-82af-f2349a0123b7' width='400'>
<img src='https://github.com/user-attachments/assets/33ba4004-3d92-4442-9a9d-ab1b62a7075e' width='400'>
</p>

# :bulb: Step 3. Insights

Conclusion:
- The limit of requests at a given moment (point) to be considered an attack is around 320 requests. If a specific time interval is considered, this value increases much more.
- The main countries of origin for attack requests are US, DE, LY and RU.
- Attacks are mainly done over HTTP 2.
- We were able to identify requests that are likely to be malicious.

Next steps:
- Try to determine which are false positives and false negatives.
- Given the situation, it is worth blocking them all, regardless of whether they are false positives or false negatives or partially mitigating them in a range that does not exceed the appropriate limit for the network. This way some real users can be maintained.
- Create an algorithm to classify malicious and non-malicious.

