import React, { useState } from 'react';
import './App.css';
import countriesData from './countries.json';

function App() {
  const [searchTerm, setSearchTerm] = useState(''); 

  const handleSearch = (event) => {
    setSearchTerm(event.target.value.toLowerCase());
  };


  const filteredCountries = countriesData.filter((country) =>
    country.country.toLowerCase().includes(searchTerm) ||
    country.capital.toLowerCase().includes(searchTerm)
  );

  return (
    <div className="App">
      <h1>Country Search</h1>
    
      <input
        type="text"
        placeholder="Search by country or capital"
        value={searchTerm}
        onChange={handleSearch}
      />
      
      
      <div>
        {filteredCountries.length > 0 ? (
          <ul>
            {filteredCountries.map((country) => (
              <li key={country.country}>
                <strong>{country.country}</strong> - {country.capital}
              </li>
            ))}
          </ul>
        ) : (
          <p>No countries found</p>
        )}
      </div>
    </div>
  );
}

export default App;
