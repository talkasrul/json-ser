# React Router DOM

React router dom adalah library kecil untuk membantu pengelolaan route pada web yang menggunakan react js.

## Cara instal

```bash
npm i react-router-dom
```
## Helper penting pada `react-router-dom`
1. BrowserRouter, untuk membungkus sebagai canvas tempat router dijalankan
2. Switch, untuk menjadikan 404 sebagai hal yang ditampilkan hanya ketika dibutuhkan saja (untuk membungkus `Route`)
3. Route, component yang dijalankan sebagai alamat yang dituju
4. Link, alamat yang akan dituju ini seperti (`<a href...`)

## Cara Pakai
```javascript
import React, { Component } from 'react'
import {
  BrowserRouter,
  Switch,
  Route,
  Link
} from 'react-router-dom'

import Home from './src/Page/Home'
import Home from './src/Page/About'
import Home from './src/Page/404'

class App extends Component {
  render() {
    return (
      <BrowserRouter>
        <React.Fragment>
          <nav>
            <li> <Link to='/'> Home </Link> </li>
            <li> <Link to='/about'> About </Link> </li>
          </nav>
          
          <main>
            <Switch>
              <Route path='/' exact component={Home} />
              <Route path='/about' exact component={Home} />          
              <Route component={404} />  
            </Switch>
          </main>
        </React.Fragment>
      </BrowserRouter>
    )
  }
}
```

## Mengirim params dari router
Init params yang akan ditrigger, contoh disini `:name`
```javascript
<Route path='/about/:name' exact component={AboutView} />
```

Init params diterima dalam `props` dengan nama `match`, lalu gunakan dengan `match.params.` + nama init params

```javascript
function AboutView({ match }) {
  return <h2>About {match.params.name} </h2>
}
```
