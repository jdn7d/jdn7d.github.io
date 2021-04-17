---
layout: post
title:      "React Project"
date:       2020-06-25 19:45:09 -0400
permalink:  deswerwerere
---

MapStateToProps and mapDispatchToProps were the two subjects I struggled to understand in the React module.

They are both part of Redux, and in order to use them you have to make sure that you are using the connect() function. This allows you to connect the state that you have in the Redux store to the components that need to use that state. 

**Connect**

To have access to those functions you have to call the connect function and pass in mapState as the first argument and mapDispatch as the second argument. 

```
export default connect(mapStateToProps, mapDispatchToProps)(Destinations)

```

**mapStateToProps**

 When using these functions, only part of the store is passed to the component, instead of having to import the entire store. In the function below, I am retreiving the state of the destinations object.
 
 `const mapStateToProps = state => {
    return {destinations: state.destinations}
}

This allows me to be able to access the destinations props in the return of that conpmonent: 
`destinations={this.props.destinations}`

**mapDispatchToProps**

This method will allow us to use the actions that we wrote in order to do things like fetching the data, adding new data, etc. With this method you can pass those methods as props in the component. 

```
const mapDispatchToProps = dispatch => {
    return {
        fetchDestinations: () => dispatch(fetchDestinationsAction()),
   }
}
``` 

With this, I can call fetchDestinations when the component mounts. 

