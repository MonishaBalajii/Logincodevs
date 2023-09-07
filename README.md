Pls send code for react with axios to admin page...inside that admin page the content is company id,company name,company url,company logo,10th aggregate,12th aggregate,deadline to apply,cost to company,required cgpa,standing arrer, eligible department and after use register button...pls give that page







//code

import React, { useState } from 'react';
import axios from 'axios';

function AdminPage() {
  const [formData, setFormData] = useState({
    companyId: '',
    companyName: '',
    companyUrl: '',
    companyLogo: null,
    tenthAggregate: '',
    twelfthAggregate: '',
    deadlineToApply: '',
    costToCompany: '',
    requiredCgpa: '',
    standingArrears: '',
    eligibleDepartment: '',
  });

  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData({
      ...formData,
      [name]: value,
    });
  };

  const handleFileChange = (e) => {
    setFormData({
      ...formData,
      companyLogo: e.target.files[0],
    });
  };

  const handleSubmit = async (e) => {
    e.preventDefault();

    try {
      const response = await axios.post('/api/addCompany', formData);
      // Handle success or any other logic here
      console.log(response.data);
    } catch (error) {
      // Handle errors here
      console.error(error);
    }
  };

  return (
    <div>
      <h1>Admin Page</h1>
      <form onSubmit={handleSubmit}>
        <div>
          <label>Company ID:</label>
          <input
            type="text"
            name="companyId"
            value={formData.companyId}
            onChange={handleChange}
          />
        </div>
        <div>
          <label>Company Name:</label>
          <input
            type="text"
            name="companyName"
            value={formData.companyName}
            onChange={handleChange}
          />
        </div>
        <div>
          <label>Company URL:</label>
          <input
            type="text"
            name="companyUrl"
            value={formData.companyUrl}
            onChange={handleChange}
          />
        </div>
        <div>
          <label>Company Logo:</label>
          <input
            type="file"
            name="companyLogo"
            onChange={handleFileChange}
          />
        </div>
        <div>
          <label>10th Aggregate:</label>
          <input
            type="text"
            name="tenthAggregate"
            value={formData.tenthAggregate}
            onChange={handleChange}
          />
        </div>
        <div>
          <label>12th Aggregate:</label>
          <input
            type="text"
            name="twelfthAggregate"
            value={formData.twelfthAggregate}
            onChange={handleChange}
          />
        </div>
        <div>
          <label>Deadline to Apply:</label>
          <input
            type="text"
            name="deadlineToApply"
            value={formData.deadlineToApply}
            onChange={handleChange}
          />
        </div>
        <div>
          <label>Cost to Company:</label>
          <input
            type="text"
            name="costToCompany"
            value={formData.costToCompany}
            onChange={handleChange}
          />
        </div>
        <div>
          <label>Required CGPA:</label>
          <input
            type="text"
            name="requiredCgpa"
            value={formData.requiredCgpa}
            onChange={handleChange}
          />
        </div>
        <div>
          <label>Standing Arrears:</label>
          <input
            type="text"
            name="standingArrears"
            value={formData.standingArrears}
            onChange={handleChange}
          />
        </div>
        <div>
          <label>Eligible Department:</label>
          <input
            type="text"
            name="eligibleDepartment"
            value={formData.eligibleDepartment}
            onChange={handleChange}
          />
        </div>
        <button type="submit">Register</button>
      </form>
    </div>
  );
}

export default AdminPage;
