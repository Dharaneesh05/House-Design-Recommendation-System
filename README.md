<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>House Design Recommendation System</title>
  <style>
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
      max-width: 800px;
      margin: 0 auto;
      padding: 20px;
      line-height: 1.6;
      color: #24292e;
    }
    h1, h2, h3 {
      border-bottom: 1px solid #eaecef;
      padding-bottom: 0.3em;
    }
    code {
      background-color: #f6f8fa;
      padding: 2px 4px;
      border-radius: 3px;
      font-family: 'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace;
    }
    pre {
      background-color: #f6f8fa;
      padding: 16px;
      border-radius: 3px;
      overflow-x: auto;
    }
    pre code {
      background: none;
      padding: 0;
    }
    ul {
      padding-left: 20px;
    }
    a {
      color: #0366d6;
      text-decoration: none;
    }
    a:hover {
      text-decoration: underline;
    }
    .highlight {
      color: #d73a49;
    }
  </style>
</head>
<body>
  <h1>House Design Recommendation System</h1>

  <h2>Introduction</h2>
  <p>The House Design Recommendation System is a web-based application that recommends 3D house models tailored to user preferences, such as architectural style, layout, size, or location. Built using a combination of Plask for motion capture, machine learning for personalized recommendations, Leaflet.js for interactive location-based maps, and Blender for creating high-quality 3D house models, this project offers an immersive experience for users to visualize and explore their ideal home designs. The system analyzes user inputs and preferences to suggest 3D models that align with their needs, enhancing decision-making in home design or real estate.</p>

  <h2>Features</h2>
  <ul>
    <li><strong>Personalized 3D House Recommendations</strong>: Suggests 3D house models based on user preferences (e.g., modern, minimalist, traditional styles, number of bedrooms, or budget).</li>
    <li><strong>Interactive Location Mapping</strong>: Uses Leaflet.js to display house model recommendations on an interactive map, allowing users to filter by geographic preferences.</li>
    <li><strong>3D Model Visualization</strong>: Renders high-quality 3D house models created in Blender, enabling users to explore designs in a browser.</li>
    <li><strong>Motion Capture Integration</strong>: Leverages Plask to incorporate motion capture for interactive 3D model navigation or virtual walkthroughs.</li>
    <li><strong>Machine Learning Recommendations</strong>: Employs machine learning algorithms (e.g., collaborative or content-based filtering) to match user preferences with house designs.</li>
    <li><strong>User-Friendly Interface</strong>: Provides a responsive and intuitive UI for inputting preferences and viewing recommendations.</li>
    <li><strong>Customizable Preferences</strong>: Allows users to specify design criteria like layout, materials, or environmental factors (e.g., eco-friendly designs).</li>
  </ul>

  <h2>Tech Stack</h2>
  <ul>
    <li><strong>Frontend</strong>: HTML, CSS, JavaScript, Leaflet.js (for interactive maps), Three.js (for 3D rendering)</li>
    <li><strong>3D Modeling</strong>: Blender (for creating and exporting 3D house models)</li>
    <li><strong>Motion Capture</strong>: Plask (for motion capture and interactive 3D navigation)</li>
    <li><strong>Machine Learning</strong>: Python, TensorFlow or Scikit-learn (for recommendation algorithms)</li>
    <li><strong>Backend</strong>: Node.js, Express.js (for API and server management)</li>
    <li><strong>Database</strong>: MongoDB (for storing user preferences, house model metadata, and recommendation data)</li>
    <li><strong>Other Tools</strong>: Git (version control), npm (package management), WebGL (for 3D rendering)</li>
  </ul>

  <h2>Installation</h2>
  <p>To set up and run the project locally, follow these steps:</p>
  <ol>
    <li><strong>Clone the Repository</strong>:
      <pre><code>git clone https://github.com/Dharaneesh05/House-Design-Recommendation-System.git
cd House-Design-Recommendation-System</code></pre>
    </li>
    <li><strong>Set Up Environment Variables</strong>:
      <p>Create a <code>.env</code> file in the <code>server</code> folder with the following:</p>
      <pre><code>PORT=5000
MONGODB_URI=mongodb://localhost:27017/house_recommendation
PLASK_API_KEY=your_plask_api_key
</code></pre>
      <p>Replace <code>your_plask_api_key</code> with your Plask API key (if applicable).</p>
    </li>
    <li><strong>Install Backend Dependencies</strong>:
      <p>Navigate to the <code>server</code> folder and install dependencies:</p>
      <pre><code>cd server
npm install</code></pre>
      <p>Required packages (included in <code>package.json</code>):</p>
      <ul>
        <li>express</li>
        <li>mongoose</li>
        <li>dotenv</li>
        <li>axios</li>
      </ul>
    </li>
    <li><strong>Install Frontend Dependencies</strong>:
      <p>Navigate to the <code>client</code> folder and install dependencies:</p>
      <pre><code>cd client
npm install</code></pre>
      <p>Required packages (included in <code>package.json</code>):</p>
      <ul>
        <li>leaflet</li>
        <li>three</li>
        <li>axios</li>
      </ul>
    </li>
    <li><strong>Set Up MongoDB</strong>:
      <ul>
        <li>Install MongoDB locally or use MongoDB Atlas for a cloud database.</li>
        <li>Ensure the <code>MONGODB_URI</code> in the <code>.env</code> file points to your MongoDB instance.</li>
        <li>Create collections for house models and user preferences. Example MongoDB schema:</li>
      </ul>
      <pre><code class="language-javascript">const houseSchema = new mongoose.Schema({
  name: String,
  style: String,
  bedrooms: Number,
  bathrooms: Number,
  area: Number,
  location: { type: { type: String }, coordinates: [Number] },
  modelUrl: String,
  materials: [String],
  createdIn: { type: String, default: 'Blender' }
});
const userPreferenceSchema = new mongoose.Schema({
  userId: String,
  preferredStyles: [String],
  preferredLocations: [{ type: String, coordinates: [Number] }],
  budget: Number,
  minBedrooms: Number
});</code></pre>
    </li>
    <li><strong>Prepare 3D Models</strong>:
      <p>Create or import 3D house models in Blender and export them as <code>.glTF</code> or <code>.OBJ</code> files. Place them in the <code>client/public/models</code> folder.</p>
    </li>
    <li><strong>Train Machine Learning Model (Optional)</strong>:
      <p>Navigate to the <code>ml</code> folder and install Python dependencies:</p>
      <pre><code>cd ml
pip install -r requirements.txt</code></pre>
      <p>Run the training script to train the recommendation model:</p>
      <pre><code>python train_model.py</code></pre>
      <p>Ensure a dataset of house models and user preferences is available (e.g., synthetic or collected data).</p>
    </li>
  </ol>

  <h2>Usage</h2>
  <ol>
    <li><strong>Run the Backend</strong>:
      <p>In the <code>server</code> folder, start the Node.js server:</p>
      <pre><code>npm run dev</code></pre>
      <p>The server will run on <code>http://localhost:5000</code>.</p>
    </li>
    <li><strong>Run the Frontend</strong>:
      <p>In the <code>client</code> folder, start the application:</p>
      <pre><code>npm start</code></pre>
      <p>The client will run on <code>http://localhost:3000</code>.</p>
    </li>
    <li><strong>Access the Application</strong>:
      <ul>
        <li>Open <code>http://localhost:3000</code> in your browser.</li>
        <li>Input preferences (e.g., architectural style, number of bedrooms, or preferred location).</li>
        <li>View recommended 3D house models rendered with Three.js.</li>
        <li>Explore house locations on an interactive map powered by Leaflet.js.</li>
        <li>Use motion capture features (via Plask) for virtual walkthroughs, if enabled.</li>
        <li>Save preferred designs to a favorites list or download model details.</li>
      </ul>
    </li>
  </ol>

  <h2>Project Structure</h2>
  <pre><code>House-Design-Recommendation-System/
├── client/                    # Frontend (JavaScript, Leaflet.js, Three.js)
│   ├── public/
│   │   └── models/            # 3D house models (.glTF, .OBJ)
│   ├── src/
│   │   ├── components/        # Reusable components (Map, 3DViewer, etc.)
│   │   ├── pages/             # Pages (Home, Preferences, Results)
│   │   └── App.js             # Main application
├── server/                    # Backend (Node.js, Express.js)
│   ├── models/                # Mongoose schemas (House, UserPreference)
│   ├── routes/                # API routes (houses, recommendations)
│   ├── index.js               # Main server file
│   └── .env                   # Environment variables
├── ml/                        # Machine learning scripts (Python)
│   ├── train_model.py         # Training script for recommendation model
│   └── requirements.txt       # Python dependencies
├── blender/                   # Blender project files for 3D models
└── README.html                # Project documentation
</code></pre>

  <h2>API Endpoints</h2>
  <ul>
    <li><strong>GET /api/houses</strong>: Fetch all house models with filters (e.g., style, location).</li>
    <li><strong>GET /api/houses/:id</strong>: Fetch details for a specific house model.</li>
    <li><strong>POST /api/recommend</strong>: Generate 3D house model recommendations based on user preferences.</li>
    <li><strong>POST /api/preferences</strong>: Save user preferences for recommendations.</li>
  </ul>

  <h2>Dataset</h2>
  <p>The project uses a custom dataset of 3D house models and metadata, including:</p>
  <ul>
    <li>House attributes (style, bedrooms, bathrooms, area, materials).</li>
    <li>Location data (geographic coordinates for mapping).</li>
    <li>User preferences (styles, budget, location) for training the recommendation model.</li>
  </ul>
  <p>3D models are created in Blender and stored as <code>.glTF</code> files. A synthetic dataset or user-collected data is used for machine learning training.</p>

  <h2>Contributing</h2>
  <p>Contributions are welcome! To contribute:</p>
  <ol>
    <li>Fork the repository.</li>
    <li>Create a new branch (<code>git checkout -b feature-branch</code>).</li>
    <li>Make your changes and commit (<code>git commit -m "Add feature"</code>).</li>
    <li>Push to the branch (<code>git push origin feature-branch</code>).</li>
    <li>Open a pull request with a detailed description of your changes.</li>
  </ol>
  <p>Please ensure your code follows the project’s coding standards and includes appropriate documentation.</p>

  <h2>License</h2>
  <p>This project is licensed under the MIT License. See the <a href="LICENSE">LICENSE</a> file for details.</p>

  <h2>Acknowledgments</h2>
  <ul>
    <li><a href="https://www.blender.org/">Blender</a> for 3D modeling tools.</li>
    <li><a href="https://leafletjs.com/">Leaflet.js</a> for interactive mapping.</li>
    <li><a href="https://plask.ai/">Plask</a> for motion capture technology.</li>
    <li>Inspired by AI-driven recommendation systems and 3D visualization projects on GitHub.</li>
  </ul>
</body>
</html>
