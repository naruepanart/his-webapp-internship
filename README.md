# HIS

## Getting Started

```bash
npm i && npm run dev
```

See : http://localhost:3000

```
[JavaScript for React Developers](https://www.youtube.com/watch?v=NCwa_xi0Uuc)

[วิธีทำให้ Code ของคุณง่ายขึ้นด้วย map(), reduce() และ filter() ใน JavaScript](https://www.techstarthailand.com/blog/detail/How-to-simplify-your-codebase-with-map-reduce-and-filter-in-JavaScript/837?fbclid=IwAR0hzyfn5EeCwSgKjL2mqvVr4O-01R471y4suj0b25TGZOBVhr2me_esSdU)

```

## Roadmap code

### การ setState

```
this.setState(prevState => ({
    isToggleOn: !prevState.isToggleOn
  }));
------------------------------------------
toggleModal = () => {
    this.setState((prevState) => ({
      isModalOpen: !prevState.isModalOpen
    }));
  }
```

### การส่งข้อมูล

```
export default class HelloWorld extends Component {
  import React, { Component } from "react"
  state = {
    message: 'Hi'
  };

  logMessage = () => {
    // This works because arrow funcs adopt the this binding of the enclosing scope.
    console.log(this.state.message);
  };

  render() {
    return (
      <input type="button" value="Log" onClick={this.logMessage} />
    );
  }
}
```

### การส่งข้อมูลข้าม components

```
import React, { Component } from "react";
import About from "./getstate";

export default class index extends Component {
  constructor(props) {
    super(props);

    this.state = {
      cart: [],
      shop: [
        { id: 35, name: "jumper", color: "red", price: 200 },
        { id: 42, name: "shirt", color: "blue", price: 15 },
        { id: 56, name: "pants", color: "green", price: 25 },
        { id: 71, name: "socks", color: "black", price: 5 },
        { id: 72, name: "socks", color: "white", price: 5 }
      ]
    };
  }

  render() {
    return (
      <div>
        {this.state.shop.map(item => (
          <About item={item} key={item.id} />
        ))}
      </div>
    );
  }
}

```

```
import React from "react";

const About = props => {
  return (
    <div>
      <p>ID : {props.item.id}</p>
      <p>Name : {props.item.name}</p>
      <p>Price : {props.item.price}</p>
    </div>
  );
};

export default About;
```

### การ post data

```
import React from "react"
import axios from "axios"

export default class PersonList extends React.Component {
  constructor(props) {
    super(props)
    this.state = {
      name: "",
    }
  }

  handleChange = e => {
    this.setState({ name: e.target.value })
  }

  handleSubmit = e => {
    e.preventDefault()

    const user = {
      name: this.state.name,
    }

    axios
      .post(`https://jsonplaceholder.typicode.com/users`, { user })
      .then(res => {
        console.log(res.data)
      })
  }

  render() {
    return (
      <div>
        <form>
          <label>
            Person Name:
            <input type="text" name="name" onChange={this.handleChange} />
          </label>
          <button type="submit" onClick={this.handleSubmit}>
            Add
          </button>
        </form>
      </div>
    )
  }
}

```

### การ get data with axios tool

```
async componentDidMount() {
    const uri = 'https://backend-jsonserver-test.herokuapp.com/users'
    const { data } = await axios.get(uri)
    this.setState({ accountusers: data })
  }
```

## ค้นหาข้อมูลใน table

```

import React, { Component } from "react"
import ToolkitProvider, { Search } from "react-bootstrap-table2-toolkit"
import BootstrapTable from "react-bootstrap-table-next"
const { SearchBar } = Search

const products = [
  {
    id: 0,
    text: "Hello:0",
    name: "Name:0",
    price: 1000,
  },
  {
    id: 1,
    text: "Hello:1",
    name: "Name:1",
    price: 1000,
  },
  {
    id: 2,
    text: "Hello:2",
    name: "Name:2",
    price: 1000,
  },
]

const columns = [
  {
    dataField: "id",
    text: "Product ID",
  },
  {
    dataField: "name",
    text: "Product Name",
  },
  {
    dataField: "price",
    text: "Product Price",
  },
]

export default class tabletest extends Component {
  render() {
    return (
      <div>
        <br />
        <br />
        <center>
          <ToolkitProvider
            keyField="id"
            data={products}
            columns={columns}
            search
          >
            {props => (
              <div>
                <SearchBar {...props.searchProps} tableId="tableId" />
                <hr />
                <BootstrapTable {...props.baseProps}/>
              </div>
            )}
          </ToolkitProvider>
        </center>
      </div>
    )
  }
}
```
