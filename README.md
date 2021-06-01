# HRBP-Class-Plus
npx create-react-app react-photo-search
cd react-photo-search
npm start
rm src/index.css
rm src/index.js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import * as serviceWorker from './serviceWorker';
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
serviceWorker.unregister();
rm src/logo.svg
nano src/App.css
nano src/App.js
import React from 'react';
import './App.css';

function App() {
  return (
    <div className="App">

    </div>
  );
}
export default App;
npm install flickr-js
nano src/App.css
* {
  box-sizing: border-box;
  background-color: rgb(244, 244, 244);
  color: #333;
  font-size: 10px;
}
* {
  box-sizing: border-box;
  background-color: rgb(244, 244, 244);
  color: #333;
  font-size: 10px;
}

.App {
  margin: 0;
  padding: 0;
}
* {
  box-sizing: border-box;
  background-color: rgb(244, 244, 244);
  color: #333;
  font-size: 10px;
}

.App {
  margin: 0;
  padding: 0;
}

.container {
  margin: 0 auto;
  max-width: 1000px;
  padding: 40px;
}
...
.container {
  margin: 0 auto;
  max-width: 1000px;
  padding: 40px;
}

.title {
  font-size: 4.4rem;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
...
.title {
  font-size: 4.4rem;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}

.form {
  display: grid;
}
...
.form {
  display: grid;
}

.label {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.input {
  font-size: 1.6rem;
  padding: 0.5rem 2rem;
  line-height: 2.8rem;
  border-radius: 20px;
  background-color: white;
  margin-bottom: 1rem;
}
...
.input {
  font-size: 1.6rem;
  padding: 0.5rem 2rem;
  line-height: 2.8rem;
  border-radius: 20px;
  background-color: white;
  margin-bottom: 1rem;
}
.button {
  background-color: rgba(0, 0, 0, 0.75);
  color: white;
  padding: 1rem 2rem;
  border: 1px solid rgba(0, 0, 0, 0.75);
  border-radius: 20px;
  font-size: 1.4rem;
  cursor: pointer;
  transition: background-color 250ms;
}
...
.button {
  background-color: rgba(0, 0, 0, 0.75);
  color: white;
  padding: 1rem 2rem;
  border: 1px solid rgba(0, 0, 0, 0.75);
  border-radius: 20px;
  font-size: 1.4rem;
  cursor: pointer;
  transition: background-color 250ms;
}

.button:hover {
  background-color: rgba(0, 0, 0, 0.85);
}
...
.button:hover {
  background-color: rgba(0, 0, 0, 0.85);
}

.card-list {
  column-count: 3;
}
...
.card-list {
  column-count: 3;
}

.card {
    margin-bottom: 1rem;
    display: flex;
}

.card--image {
    flex: 100%;
    margin-top: 1rem;
    border-radius: 10px;
}
...
.card--image {
    flex: 100%;
    margin-top: 1rem;
    border-radius: 10px;
}

@media (min-width: 768px) {
  .form {
    grid-template-columns: auto 1fr auto;
    grid-gap: 1rem;
    align-items: center;
  }
  .input {
    margin-bottom: 0;
  }
}

@media only screen and (max-width: 600px) {
    .card-list {
        column-count: 1;
    }
}
nano src/App.js
import React from 'react';
import './App.css';

function App() {
  return (
    <div className="App">
      <div className="container">
        <h1 className="title">React Photo Search</h1>
      </div>
    </div>
  );
}
import React from "react";

export default function SearchPhotos() {
  return (
    <>

    </>
  );
}
nano src/App.js
import React from "react";
import "./App.css";
import SearchPhotos from "./searchPhotos"

function App() {
  return (
    <div className="App">
      <div className="container">
        <h1 className="title">React Photo Search</h1>
        <SearchPhotos />

      </div>
    </div>
  );
}
export default App;
...
export default function SearchPhotos() {
  return (
    <>
      <form className="form"> 
        <label className="label" htmlFor="query"> 
          {" "}
        </label>
        <input
          type="text"
          name="query"
          className="input"
          placeholder={`Try "dog" or "apple"`}
        />
        <button type="submit" className="button">
          Search
        </button>
      </form>
    </>
  );
}
nano src/searchPhotos.js
import React, { useState } from "react";

export default function SearchPhotos() {
...
useState(initialState)
const [query, setQuery] = useState(initialState);
...

export default function SearchPhotos() {
  const [query, setQuery] = useState("");

  return (
    <>
      <form className="form">
        <label className="label" htmlFor="query">
          {" "}
     
        </label>

<input
    type="text"
    name="query"
    className="input"
    placeholder={`Try "dog" or "apple"`}
    value={query}
    onChange={(e) => setQuery(e.target.value)}
/>
...
...
export default function SearchPhotos() {
   const [query, setQuery] = useState("");
   console.log(query);

  return (
    <>
    //
    </>
  );
}
import React, { useState } from "react";
export default function SearchPhotos() {
  const [query, setQuery] = useState("");
  console.log(query);

  return (
    <>
      <form className="form">
        <label className="label" htmlFor="query">
          {" "}
        </label>
        <input
          type="text"
          name="query"
          className="input"
          placeholder={`Try "dog" or "apple"`}
          value={query}
          onChange={(e) => setQuery(e.target.value)}
        />
        <button type="submit" className="button">
          Search
        </button>
      </form>
    </>
  );
}
import React, { useState } from "react";
import flickr, { toJson } from "flickr-js";
import React, { useState } from "react";
import Unsplash, { toJson } from "flickr-js";

const flickr = new flickr({
  accessKey: "your_Access_Key",
});
...
export default function SearchPhotos() {
  const [query, setQuery] = useState("");

  const searchPhotos = async (e) => {
    e.preventDefault();
    console.log("Submitting the Form")
  };
...
  return (
    <>
      <form className="form" onSubmit={searchPhotos}>
...
search.photos(keyword, page, per_page, filters)
...
const searchPhotos = async (e) => {
  e.preventDefault();
  flickr.search
    .photos(query)
    .then(toJson)
    .then((json) => {
      console.log(json);
    });
};
...
{
  "results": [{
     "description": "Pink Wall Full of Dogs",
     "alt_description": "litter of dogs fall in line beside wall",
     "urls": {
           "raw": "https://www.flickr.com/photos/vwalters10/30735855818/in/photolist-NQ2i7A-5YDW4w-cJDDcY-AMqcpU-xt9F9h-xtXSWV-cJDDjq-pwe2cA-pgM8vp-efZ1jJ-at1xk7-cJDCub-4ntabX-2d2yJwD-DGNtCc-2a6nozA-kBS1DB-oPHFaW-b4rBSv-Tb81P3-GgvkjS-kBR3qr-JsjqrL-qWSPpP-bUG9Ls-9hMyN4-kBQEkV-kBRpS4-rV85K9-kBT78S-5v9jL1-e1J2bL-25xpt9L-PVJFk-WmLNA9-pCJGC3-cJDCpj-kBRtcD-dRm5ih-dSvags-oMJmPw-nxJwHc-bj6bg-iTmyAJ-Se55LF-am5L91-dS114C-9o1mXS-Jsjsym-dSvbhq",
           "full": "https://www.flickr.com/photos/35209345@N02/3266551852/in/photolist-NQ2i7A-5YDW4w-cJDDcY-AMqcpU-xt9F9h-xtXSWV-cJDDjq-pwe2cA-pgM8vp-efZ1jJ-at1xk7-cJDCub-4ntabX-2d2yJwD-DGNtCc-2a6nozA-kBS1DB-oPHFaW-b4rBSv-Tb81P3-GgvkjS-kBR3qr-JsjqrL-qWSPpP-bUG9Ls-9hMyN4-kBQEkV-kBRpS4-rV85K9-kBT78S-5v9jL1-e1J2bL-25xpt9L-PVJFk-WmLNA9-pCJGC3-cJDCpj-kBRtcD-dRm5ih-dSvags-oMJmPw-nxJwHc-bj6bg-iTmyAJ-Se55LF-am5L91-dS114C-9o1mXS-Jsjsym-dSvbhq/",
           "regular": "https://www.flickr.com/photos/primerx24/7702561586/in/photolist-NQ2i7A-5YDW4w-cJDDcY-AMqcpU-xt9F9h-xtXSWV-cJDDjq-pwe2cA-pgM8vp-efZ1jJ-at1xk7-cJDCub-4ntabX-2d2yJwD-DGNtCc-2a6nozA-kBS1DB-oPHFaW-b4rBSv-Tb81P3-GgvkjS-kBR3qr-JsjqrL-qWSPpP-bUG9Ls-9hMyN4-kBQEkV-kBRpS4-rV85K9-kBT78S-5v9jL1-e1J2bL-25xpt9L-PVJFk-WmLNA9-pCJGC3-cJDCpj-kBRtcD-dRm5ih-dSvags-oMJmPw-nxJwHc-bj6bg-iTmyAJ-Se55LF-am5L91-dS114C-9o1mXS-Jsjsym-dSvbhq/",
           "small": "https://www.flickr.com/photos/decadesoflife/21407073886/in/photolist-yBERfN-gQQQv-ASfp2-23otTz9-e3o7RD-5T5RV3-VuUh9G-NLgrtQ-U4JGTa-2ep8M27-axeKT4-AoQG9-tbY2XD-KA4XwC-ZrLYc7-JySHr-bjrS9p-2fG5Li6-GaJfsB-dTp6UA-MKHAVS-KyEd6B-5vUH1R-5m4MF6-ccgBrY-MAm7di-puYVZN-6aGqrp-anZkBm-zwFQ8C-7YYct2-oheAC8-2PNMmM-hPEa2-ozZzWu-f7XyVn-2bgJeJg-cHBshu-HGjbYR-yBcnRb-t2U3jD-8iB8P8-GTWdHw-CaWWR-6jyryT-W57PwA-3NUaKJ-78jYwf-ayKG8y-LPn9Yg",
           
                },
    ...
}
...
  const [query, setQuery] = useState("");
  const [pics, setPics] = useState([]);

    flickr.search
      .photos(query, 1, 20)
      .then(toJson)
      .then((json) => {
        setPics(json.results);
  });
        <button type="submit" className="button">
          Search
        </button>
      </form>
      <div className="card-list">
      </div>
    </>
  );
}
...
        <button type="submit" className="button">
          Search
        </button>
      </form>
      <div className="card-list">
        {pics.map((pic) => pic.id )}
      </div>
    </>
  );
}
        <button type="submit" className="button">
          Search
        </button>
      </form>
      <div className="card-list">
        {
          pics.map((pic) => <div className="card"></div>);
        }
      </div>
    </>
  );
}
        <button type="submit" className="button">
          Search
        </button>
      </form>
      <div className="card-list">
        {
          pics.map((pic) =>
            <div className="card">
              <img
                className="card--image"
                alt={pic.alt_description}
                src={pic.urls.full}
                width="50%"
                height="50%"
              ></img>
            </div>);
        }
      </div>
    </>
  );
}
...
      <div className="card-list">
        {pics.map((pic) =>
          <div className="card" key={pic.id}>
            <img
              className="card--image"
              alt={pic.alt_description}
              src={pic.urls.full}
              width="50%"
              height="50%"
            ></img>
          </div>)};
      </div>
    </>
  );
}
