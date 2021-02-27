# LiveData-Made-Easy

LiveData is basically a data holder that follows the observer pattern. LiveData subjects/objects maintain a list of their observers and notify them of state changes.

**LiveData is lifecycle-aware**
## What is a life cycle aware component?
A life cycle aware component is a component that is aware of other components like activity or fragment and performs some action in response to change in this component's life cycle status.

Before LiveData notifies any observer, it will check if the observer is live or not. If it is life, then the notification will be sent; otherwise, not. There is no need to unsubscribe observers with LiveData.

## Instance of LiveData


