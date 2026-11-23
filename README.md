# 📌 Real Estate Scraping and Indexing Project  

This project scrapes property listings from a real estate portal and indexes them in **Elasticsearch** for fast, efficient searches. It uses **Node.js**, **PostgreSQL** and **Elasticsearch**.  

---  

## ✅ Requirements  

Before you start, make sure you have the following software installed:  

- [Git](https://git-scm.com/downloads/win)  
- [Node.js](https://nodejs.org/) (version 16+)  
- [PostgreSQL](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)  
- [Elasticsearch](https://www.elastic.co/downloads/elasticsearch)    

---  

## 📌 Installation  

### 1️⃣ Clone the repository  
First, open the terminal and run the command below to clone the project repository:  
```sh
git clone https://github.com/MickaelWenicio/Projeto-Captei.git
```
Then go into the project folder:  
```sh
cd Projeto-Captei
```

---  

### 2️⃣ Install and configure **PostgreSQL**  
1. Download and install PostgreSQL from the [official website](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads).  
2. By default the project uses the `postgres` user, which is the database's default user.  
3. Rename the project's `example.env` file to `.env` and set your database password:  
   ```env
   DB_PASSWORD=your_password
   ```  

---  

### 3️⃣ Install and configure **Elasticsearch**  

#### IMPORTANT!! Follow the order below exactly for it to work correctly.

1. Download Elasticsearch from the [official website](https://www.elastic.co/downloads/elasticsearch).  
2. Extract the downloaded file to a directory of your choice.  
3. Open the extracted folder, go into the **bin** directory and double-click `elasticsearch.bat`.  
4. Wait for the process to finish, and once it has, **close Elasticsearch**.  
5. In the **PROJECT** directory, open the `elasticsearch` folder.    
   - Inside it there is only one folder, named **`config`**, containing a single file.  
6. **Copy** that file.  
7. Now go to the folder where you **extracted** Elasticsearch.  
8. Inside the extracted folder, find the `config` directory, open it and **paste the copied file**, replacing the existing one.  
9. To start Elasticsearch, go back to the `bin` folder inside the extracted directory and **run** `elasticsearch.bat`:  
10. Wait for Elasticsearch to start and test it by opening [http://localhost:9200](http://localhost:9200) in your browser.  
    If it is working, it will show a JSON response with information about the service.  

---  

### 4️⃣ Install the project dependencies  
With **Node.js** installed, go to the project folder and run:  
```sh
npm install
```  

---  

## 🚀 Running the Project  

### 🔹 Start the application  
To run the application, use:  
```sh
npm start
```  
The application is now running! 🎉 The project will create the required index, database and tables.  

---  

## 👀 Viewing the Data  

After starting the application, you can view the property data indexed in Elasticsearch in several ways:  

### 1️⃣ In the browser  
- Open a specific document in Elasticsearch directly by appending the desired property ID to the base URL:  
  **Example:**  
  `http://localhost:9200/imoveis/_doc/imovel_12`  
  This returns a JSON document like the example below:  
  ```json
  {
    "_index": "imoveis",
    "_id": "imovel_12",
    "_version": 1,
    "_seq_no": 12,
    "_primary_term": 1,
    "found": true,
    "_source": {
      "id": "12",
      "titulo": "Apartamento com 3 quartos no centro",
      "descricao": "Descrição detalhada do imóvel...",
      "url": "https://exemplo.com/imovel_12",
      "tipoNegocio": "Venda",
      "endereco": "Rua Exemplo, 123",
      "preco": 500000,
      "quartos": 3,
      "banheiros": 2,
      "vagas_garagem": 1,
      "area_util": 80,
      "capturado_em": "2023-10-01T12:00:00Z",
      "atualizado_em": "2023-10-01T12:00:00Z"
    }
  }
  ```  

### 2️⃣ With tools like **Insomnia** or **Postman**  
- Send a **GET** request to the Elasticsearch API:  
  **URL:** `http://localhost:9200/imoveis/_search`  
  **Request body (JSON):**  
  ```json
  {
    "query": {
      "match_all": {}
    },
    "from": 0,
    "size": 120
  }
  ```  
  This returns all indexed properties (up to 120 documents) as JSON.  

### 3️⃣ With **Kibana** (optional)  
- If you use Kibana, you can use **Dev Tools** to run queries directly against Elasticsearch.  
  **Example query:**  
  ```json
  GET /imoveis/_search
  {
    "query": {
      "match_all": {}
    }
  }
  ```  

---  
