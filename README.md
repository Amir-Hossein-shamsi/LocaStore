
# 🌍 LocaStore

> An interactive geospatial tool built with **Jupyter**, **ipyleaflet**, and **MongoDB** for searching, selecting, and storing geographic locations.

[![Python](https://img.shields.io/badge/python-3.6%2B-blue)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-%23F37626.svg?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?logo=mongodb&logoColor=white)](https://www.mongodb.com/)

---

## ✨ Features

- 🗺️ **Interactive Map**: Powered by `ipyleaflet`, centered on Tehran.
- 🔍 **Address Search**: Leverages Nominatim via `geopy` for geocoding.
- 🎯 **Draggable Marker**: Place and move markers with ease.
- 🛠️ **Smart Address Handling**: Automatically detects manual marker movement and labels as "custom".
- 💾 **MongoDB Integration**: Store confirmed locations directly in MongoDB.
- 📂 **Data Retrieval**: Easily fetch and display stored locations from the database.

---

## 🧰 Requirements

Ensure you have the following installed:

- Python 3.6+
- Jupyter Notebook
- MongoDB (locally or via Docker)
- Required Python packages:

```bash
pip install ipyleaflet geopy ipywidgets pymongo
```

---

## 🐳 Using Docker Compose for MongoDB

A ready-to-use `docker-compose.yml` is included for spinning up MongoDB quickly.

### 📄 `docker-compose.yml`

```yaml
version: '3.8'

services:
  mongo:
    image: mongo:4.4
    container_name: mongodb
    restart: unless-stopped
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: root
    volumes:
      - mongo_data:/data/db

volumes:
  mongo_data:
```

### ▶️ Start MongoDB

```bash
docker-compose up -d
```

This will launch MongoDB on port `27017` with credentials:

- **Username:** `root`
- **Password:** `root`

---

## 🚀 Usage

1. **Start MongoDB**  
   Ensure MongoDB is running locally (use Docker Compose if needed).

2. **Open the Notebook**  
   Launch `main.ipynb` in Jupyter Notebook.

3. **Search for an Address**  
   - Type an address in the input field and click **Search**.
   - The map centers on the location, placing a draggable marker.

4. **Move the Marker (Optional)**  
   - Drag the marker to fine-tune the position.
   - The address input will update to `"custom"`.

5. **Confirm the Location**  
   - Click **Confirm** to save the coordinates and address to MongoDB.

6. **View Stored Locations**  
   - Use the notebook to retrieve and display all saved locations.

---

## 🧪 Example

Search for `"Tehran University"`, adjust the marker if needed, and confirm. The system will store:

- Coordinates
- Address (or `"custom"` if manually moved)

---

## 📁 File Structure

```
LocaStore/
├── main.ipynb          # Main Jupyter notebook
├── docker-compose.yml  # MongoDB setup
└── README.md           # This file
```

---

## 📝 Notes

- Default MongoDB credentials are hardcoded for local development. Update them as needed.
- Designed for demonstration and educational purposes.

---

## 👨‍💻 Author

**AmirHossein Shamsi**  
[GitHub](https://github.com/Amir-Hossein-shamsi) | [Email](mailto:shamsiamirhossein1@gmail.com)

---

## ❤️ Contributions

Feel free to fork, submit issues, or make pull requests!
