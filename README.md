# LocaStore

A Jupyter-based interactive geospatial tool for searching, selecting, and storing geographic locations using a map interface, address search, and MongoDB.

---

## Features

- **Interactive Map**: Uses `ipyleaflet` to display a map centered on Tehran.
- **Address Search**: Enter an address and search using Nominatim geocoding.
- **Draggable Marker**: After searching, a marker is placed on the map. You can drag the marker to a custom location.
- **Custom Address Handling**: If you move the marker after searching, the address input automatically changes to "custom".
- **MongoDB Integration**: Confirming a location stores the coordinates and address (or "custom") in a MongoDB collection.
- **Data Retrieval**: Fetch and display all stored locations from MongoDB.

---

## Requirements

- Python 3.6+
- Jupyter Notebook
- MongoDB (running locally or via Docker Compose)
- The following Python packages:
  - ipyleaflet
  - geopy
  - ipywidgets
  - pymongo

Install dependencies with:

```bash
pip install ipyleaflet geopy ipywidgets pymongo
```

---

## Using Docker Compose for MongoDB

You can easily run MongoDB locally using Docker Compose.  
A `docker-compose.yml` file is included in this project:

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

### Start MongoDB with Docker Compose

```bash
docker-compose up -d
```

This will start a MongoDB instance on port `27017` with username `root` and password `root`.

---

## Usage

1. **Start MongoDB**  
   Make sure MongoDB is running locally with a user `root` and password `root`.  
   You can use Docker Compose as described above.

2. **Open the Notebook**  
   Open `main.ipynb` in Jupyter Notebook.

3. **Search for an Address**  
   - Enter an address in the input box and click "Search".
   - The map will center on the found location and place a draggable marker.

4. **Move the Marker (Optional)**  
   - Drag the marker to a new location if desired.
   - The address input will change to "custom" to indicate a manual selection.

5. **Confirm the Location**  
   - Click "Confirm" to store the location and address in MongoDB.

6. **View Stored Locations**  
   - The notebook can fetch and print all stored locations from the database.

---

## Example

- Search for "Tehran University", move the marker, and confirm. The database will store the coordinates and address ("custom" if moved).

---

## File Structure

- `main.ipynb`: Main notebook with all interactive code.
- `docker-compose.yml`: Docker Compose file for MongoDB.
- `README.md`: This file.

---

## Notes

- The MongoDB URI and credentials are hardcoded for local development. Adjust as needed for your environment.
- The notebook is set up for demonstration and educational purposes.

---

**Author:**  
AmirHossein Shamsi
