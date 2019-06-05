# canopy-listing
A Canopy UI framework for listing resources.

Loading the list, saving the resource, and displaying the grid all built-in to the class. You will need to add edit functionality to the columns.

The form for creation and editing should be put into the overlay. Make sure to have a column defined for an edit button.


```
import React from 'react'
import Listing from '@essappstate/canopy-listing'
import PetForm from './PetForm'

class PetListingClass extends Listing {
  constructor(props) {
    super(props)
    this.restUrl = 'mycanopymodule/Admin/Pets/'
    this.label = 'Pets'
    this.defaultResource = {
      id: '0',
      petName: '',
    }
    
    // callback is not required
    this.columns = [
      {
        column: 'options',
        callback: (row, key) => {
          return (
            <a href="#" onClick={
              this.editResource.bind(this, key)
            }>Edit</a>
          )
        }
      },
      {
        column: 'petName',
        label: 'Pet name',
        callback: (value, key) => return (
          <a href="#">{value.petName}</a>),
        style: {width: '10%'}
      }
    ]
    this.state.resource = Object.assign({}, this.defaultResource)
    }
    
    // not required
    title() {
        return <h2>My Pets</h2>
    }
    
    
    overlay() {
        return {
          content: <PetForm resource={this.state.resource}/>,
          close: this.load
        }
    }
}

```
