/* eslint-disable import/extensions */
/* eslint-disable import/no-unresolved */
import { Sequelize, DataTypes } from 'sequelize';
import { unlinkSync } from 'node:fs';
import getAllChildHashes from './fs-crawler.js';
import dotenv from 'dotenv'
dotenv.config()
console.log(process.env);
const sequelize = new Sequelize(process.env.DATABASE, process.env.DB_USERNAME, process.env.DB_PASSWORD, {
  host: process.env.MYSQL_IP,
  dialect: 'mysql',
  logging: false,
});
export const Book = sequelize.define('book', {
  name: DataTypes.STRING,
  hash: {
    type: DataTypes.STRING,
    primaryKey: true,
  },
  path: DataTypes.INTEGER,
});

export const pathTags = sequelize.define('path_tags', {
  id: {
    type: DataTypes.INTEGER,
    autoIncrement: true,
    primaryKey: true
  },
  path: {
    type: DataTypes.STRING,
    primaryKey: true,
  },
});

export async function IniDb() {
  try {
    await sequelize.authenticate();
    await sequelize.sync();
  } catch (error) {
    // eslint-disable-next-line no-console
    console.error('Unable to connect to the database:', error);
  }
}
/**
 * @param  {} path path where it will crawl ower children and add to db. duplicate gets removed
 */
export async function updateLibrary(path) {
  const hashes = await getAllChildHashes(path);
  // creat db models from children in "path"

  let tag = creattag(x.path);
  let pathtag = pathTags.findOne({ where: { path: tag }, raw: true });
  if (!pathtag) {
    pathtag = pathTags.upsert({
      path: path
    })
  }
  const bookModels = hashes.map(async (x) => Book.build({ name: x.name, hash: x.hash, path: x.path, tag: await creattag(x.path).id }));
  bookModels.forEach(async (element) => {
    try {
      // saves to db
      await element.save();
    } catch (error) {
      // delete files with duplicate hash
      if (error.original.errno === 1062) {
        const book = await Book.findOne({ where: { path: element.path }, raw: true });
        // if it got matching path its already added
        if (!book) {
          console.log('err1', `delete ${element.path}`);
          unlinkSync(element.path);
        }
      } else {
        console.log("1", error);
      }
    }
  });
}
async function creattag(pathString) {
  console.log("path", pathString);
  const path = pathString.split("/")
  let tags = []
  let tagStart = false
  let depth = process.env.TAG_DEPTH || 0
  for (let index = 0; index < path.length; index++) {
    const element = path[index];
    // will make all dir before TAGSTART not be part of formated string
    if (element == process.env.TAGSTART) {
      tagStart = true
    }
    // after Folder trigger add next 3 folder name to tag name
    if (tagStart) {
      if (depth < 3) {
        tags.push(element)
        depth++;
      }
    }
  }
  console.log(tags.join("/"));
  let cutTag = tags.join("/");
  let pathtag = pathTags.findOne({ where: { path: cutTag } });
  if (!pathtag) {
    pathtag = await pathTags.upsert({
      path: path
    })
  }
  return pathtag
}






import type { AppProps } from 'next/app'

function MyApp({ Component, pageProps }: AppProps) {
  return <div>
    <Component {...pageProps} />
    <style jsx global>{`
      html,
      body {
        padding: 0;
        margin: 0;
        font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto,
          Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue,
          sans-serif;
      }
      * {
        box-sizing: border-box;
      }
    `}</style>
  </div>
}

export default MyApp


import { useState, useEffect } from "react";

const MainPage = () => {
  const [dark, setDark] = useState(false);
  useEffect(() => {
    const darkMode = window.matchMedia('(prefers-color-scheme: dark)');
    console.log(darkMode.matches);
    setDark(darkMode.matches)
  }, []);

  return (
    <main>
      <div className="container">
        <h2>
          Roles
        </h2>
        <p>
          Since 2017
          Full Stack: Have architected, developed, and shipped fullstack projects. Worked in small teams and followed tight deadlines
        </p>
        <p>
          since 2021
          Web3 and blockchian: Freelanced on multiple web3 blockchains and profficent with rust and webassembly
        </p>
        <p>
          2017-2021
          Have created view and follow bots for social media, data scraping and webcrawlers
        </p>
        <p>
          system administrator: since 2011
          Lived and breated linux for over a decade. Worked with dedicated servers and advanced security knowledge.
        </p>
        <h2>
          INDUSTRY EXPERIENCE
        </h2>
        <p>
          Onlineklipp aug 2017 november 2018
          - Started as a small startup to find and compare prices for barbers.
          - tasks was fullstack and webscraping. Deployed and maintained a cluster of server deployed on Linux dedicated servers.
          - stack: Express Mongodb nginx and vuejs
        </p>
        <p>
          Remote: Aniwatch feb 2019-2021 july
          large streaming videostreaming. Worked mostly on the frontend and the rest api.
          - maintaing the api
          - Delivering scalable Front End
          - Stack: Express mysql and react with embeded video
        </p>
        <p>
          Twitch/Youtube Livestream viewbotting
          Sold it as a service to established sites. Hosted on physical selfbuilt linux server.
          - creating and selling Sas
          - Complex headless browsers made in puppeteer and playwright
        </p>
        <p>
          h1z1hunt.com 2016 - 2019
          - https://www.youtube.com/watch?v=9xFr1DB9NuY
          - frontend
          - sockets and react
        </p>
      </div>
      <div id="grid-container">
        <span>
          <h2>
            Showcase:
          </h2>

          <p>
            {" secretsloth.com Bookbook.com"}
          </p>
        </span>
        <span>
          <h2>
            TECH SKILLS
          </h2>
          <p>
            Typescript JavaScript Rust C++ C# NodeJS HTML SCSS SQL Mongodb React Nextjs Pupeteer Playwright Docker Websockets
          </p>
        </span>
      </div>
      <nav>
        <button className="dark-mode-btn" onClick={() => setDark(!dark)}>{dark ? "☀️" : "🌙"}</button>
      </nav>
      <style jsx global>{`
              :root {
                --bg:${dark ? "black" : "white"};
                --text:${dark ? "white" : "black"};
              }
              body{
                background-color: var(--bg)                                
              }
              main{
                
              }
              .container{
                display:flex;
                flex-wrap: wrap;
                flex-direction: column;
                align-items: center;

              }
              .grid-container{
                display: grid;
                grid-template-columns: 1fr 1fr
                margin-left: 15vw;
                margin-right: 15vw;
              }
              h2{
              }
              p,h2,span{
                width: 50%;
              }
              p,h2{
                color: var(--text);
              }
              button{
                position: absolute;
                top: 1vh; left:1vw;
                background: none;
                color: inherit;
                border: none;
                padding: 0;
                font: inherit;
                cursor: pointer;
                outline: inherit;

                font-size: 2vw;
              }
              @media screen and (max-width: 992px) {
                main{
                  margin-left: 0;
                  margin-right: 0;
                }
                p,h2{
                width: 100%;
              }
              }
      `}</style>
    </main>
  )
};
export default MainPage
