# LiveData-Made-Easy

LiveData is basically a data holder that follows the observer pattern. LiveData subjects/objects maintain a list of their observers and notify them of state changes.

**LiveData is lifecycle-aware**
## What is a life cycle aware component?
A life cycle aware component is a component that is aware of other components like activity or fragment and performs some action in response to change in this component's life cycle status.

Before LiveData notifies any observer, it will check if the observer is live or not. If it is alive, then the notification will be sent; otherwise, not. There is no need to unsubscribe observers with LiveData.

## Instance of LiveData

MutableLiveData that will be used for updating the variable *name*
```kotlin
private MutableLiveData<String> name;
```
### MutableLiveData has two public methods
```kotlin
1. void postValue(T value)
```
This method works on both the **main and brackground thread**
```kotlin
2. void setValue(T value)
```
This only works on main thread.

### Code for updating LiveData using setValue and postValue
```kotlin
name.setValue(/**updated data**/)  // main and background thread

OR

name.postValue(/**updated data**/) // main thread only
```
One either one of these is called, any observers will be updated accordingly.

## Observers
### Assuming that our data is inside a viewModel
```kotlin
class MainViewModel: ViewModel() {

    init {
        getName()
    }
    lateinit var name: MutableLiveData<String>
    
    private fun getName() {
        name = MutableLiveData()
        name.postValue("Jonny")
    }
    ...
```

### The Observer(s)
```kotlin
 // ViewModel Instanct
 val mainViewModel = ViewModelProvider(this,).get(MainViewModel::class.java)
 
 //Observer
 mainViewModel.name.observe(this, { 
            name -> 
            // if there is a change in data then that data will be reflected to all the observers
})
```
