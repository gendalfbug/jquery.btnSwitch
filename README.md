## jquery.btnSwitchWCC (with ConfirmCall)
[![NPM version](http://img.shields.io/npm/v/jquery-btnswitch.svg?style=flat)](https://www.npmjs.com/package/jquery-btnswitch)
[![npm](https://img.shields.io/npm/l/jquery-btnswitch.svg)](https://www.npmjs.com/package/jquery-btnswitch)
[![npm](https://img.shields.io/npm/dt/jquery-btnswitch.svg)](https://www.npmjs.com/package/jquery-btnswitch)

jquery.btnswitchwcc.js (fork)<br/>
     Minimal Usage: 
   ```javascript
     $( document ).ready(function() {
        $('.btn-switch').each(function () {
            $('#' + this.id).btnSwitchWCC({
                Theme: 'iOS',
                ToggleState: $(this).attr('ToggleState'),
                ConfirmChanges: true,
                ConfirmCall: showModal.bind(this,this, switchState.bind(this, this))
            });
        });
    });
    
    /**
    // bootstrap modal
    <div class="modal" id="confirmModal">
    ...
                <div class="modal-footer">
                <button type="button" class="btn btn-default" data-dismiss="modal">No</button>
                <a href="javascript:void(0);"  id="form-url" class="btn btn-success pull-right"
                   title="submit">
                    Yes
                </a>
            </div>
    ...
    </div>
     */
     
  function showModal(element, callback, callbackSwitch) {
        if (callbackSwitch == undefined) callbackSwitch = function () {};

        //open modal
        var _modal  = $("#confirmModal");
        _modal.modal();
        _modal.find('#form-text').html( element.getAttribute('data-text'));

        // add event
        var _formUrl = _modal.find('#form-url');
        _formUrl.attr('data-url', element.getAttribute('data-url') );
        _formUrl.off('click');
        _formUrl.on('click', callback.bind(this, callbackSwitch.bind(this)));
    }
    
    function switchState(element, callbackSwitch) {
        if (callbackSwitch == undefined) callbackSwitch = function () {};

        $.post('\your_ajax\url', {
       your_data: 'your_value'
        }, function (data) {
          
        }).done(function () {
            callbackSwitch(true);
        }).fail(function () {
            callbackSwitch(false);
        });
        return false;
    }
    
   ```
   ## discription
   ConfirmCall: showModal.bind(this,this, switchState.bind(this, this), HERE WILL BE ADDED A CALLBACK )
   
or jquery.btnswitch.js (origin)<br/>
     Minimal Usage: 
   ```javascript
   $('#switch').btnSwitch()
   ```
```javascript
 Settings:
 Theme: Select a theme (Button, Light, Swipe, iOS, Android)
 OnText: What to display for the "On" Button
 OffText: What to display for the "Off" Button
 OnValue: The value of the "On" Button
 OffValue: The value of the "Off" Button
 OnCallback: Callback on "On" selection
 OffCallback: Callback on "Off" selection
 ConfirmCall: Callable before switch use with ConfirmChanges,
 ToggleState: Set the state of the switch toggle
 ConfirmChanges: Determines if we should confirm any changes
 ConfirmText: What message we'll display to the user when ConfirmChanges is set to true
 HiddenInputId: the hidden field the plugin should populate or false to not populate a hidden field
```
A simple way to create button switches

look for examples and details at: https://eman1986.github.io/jquery.btnSwitch/
