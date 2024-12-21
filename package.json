import React, { useState } from "react";
import axios from "axios";

function BodyDimensionsApp() {
const [image, setImage] = useState(null);
const [dimensions, setDimensions] = useState(null);

const handleImageChange = (e) => {
setImage(e.target.files[0]);
};

const handleSubmit = async (e) => {
e.preventDefault();
if (!image) return alert("Please upload an image.");

const formData = new FormData();
formData.append("file", image);

try {
const response = await axios.post("http://<backend-api-endpoint>/api/calculate", formData);
setDimensions(response.data);
} catch (error) {
console.error("Error calculating dimensions:", error);
}
};

return (
<div>
<h1>Body Dimensions Calculator</h1>
<form onSubmit={handleSubmit}>
<input type="file" accept="image/*" onChange={handleImageChange} />
<button type="submit">Calculate Dimensions</button>
</form>
{dimensions && (
<div>
<h2>Calculated Dimensions</h2>
<ul>
{Object.entries(dimensions).map(([key, value]) => (
<li key={key}>
{key}: {value}
</li>
))}
</ul>
</div>
)}
</div>
);
}

export default BodyDimensionsApp;