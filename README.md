# 🛡️ AI-Driven Proactive Phishing Detection and Early Warning System
 
> 🔒 **Repository Privacy Notice:** > Please note that because this project was developed as part of an official corporate internship program and is integrated with internal company systems, the source code cannot be shared publicly due to confidentiality policies. If you are an academic evaluator who wishes to review the code, please contact me, and I would be happy to grant you collaborator access.
 
## 📌 Project Overview
This project is an end-to-end cybersecurity architecture that utilizes machine learning algorithms to predict potential phishing URLs, identify corporate brands targeted by cyber attackers, and execute real-time automated alert mechanisms against active threats.
 
The project incorporates both a robust data processing and event-driven notification infrastructure based on **Java/Spring Boot**, and an advanced machine learning prediction layer based on **Python**.
 
## 🏗️ Architecture & Core Layers
The developed system consists of 4 integrated primary layers:
 
* **1. Data Processing Layer (Java & Spring Boot):** Processes a dataset comprising over 500,000 historical phishing URLs. Multi-table data is merged, redundant records are eliminated, and a high-performance CSV dataset is exported for model training with minimal system resource consumption.
* **2. Machine Learning Layer (Python):** 
* **Phase 1 (Brand Detection):** **DBSCAN** and **HDBSCAN** clustering algorithms are applied to the training data to detect and cluster specific corporate brands targeted by attackers (yielding between 35-40 distinct brands).
* **Phase 2 (URL Generation and Validation):** Potential new phishing URL patterns are generated using **LSTM** networks.These generated addresses are then processed through a pre-trained **Random Forest** model (trained on the characteristics of a phishing URL) for validation. Only URLs with a high confidence/accuracy rate are securely stored in the MongoDB database.
* **3. Access Control Layer:** The real-time status and accessibility of these potential URLs in the MongoDB database are periodically tested via scheduled tasks.
* **4. Notification Layer (Apache Kafka):** Malicious URLs detected as accessible are immediately dispatched to an **Apache Kafka** event bus to trigger automated alerts for the relevant cybersecurity incident response teams in real-time.
 
## 🛠️ Technologies & Tools Used
* **Backend & Data Processing:** Java 21, Spring Boot 
* **Machine Learning & AI:** Python, LSTM (TensorFlow/Keras), Random Forest, DBSCAN, HDBSCAN (Scikit-learn)
* **Database / Storage:** MongoDB
* **Event Streaming & Messaging:** Apache Kafka 
* **Workflow:** RESTful APIs, Scheduled Tasks, Event-driven Architecture
 
### Prerequisites
- JDK 21+
- Python 3.2+
- MongoDB instance running
- Apache Kafka cluster running
 
### 1. Running the Data Processing (Java/Spring Boot)
```bash
cd backend-service
./mvnw clean install
./mvnw spring-boot:run
