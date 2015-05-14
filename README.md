sNotes
======

A javascript library using jQuery for using online interactive sticky notes on www sites.

How to initialize sNotes example
================================

Basic initialization is very simple and lightweight.

    jQuery(document).ready(function() {
      sNotes.init(); // that's all :)
    });

Need custom callbacks? Sure
===========================

You can use several callbacks, after the note was **created**, **moved**, **resized**, **edited** or **deleted**. In example below, there is used only one method `saveNotes()` for all callbacks. Simply, after each action all notes are saved, just for sure.

    jQuery(document).ready(function() {
      var settings = {
        callbacks: {
          created: (function(note) { saveNotes(sNotes.getAll()); }),
          moved: (function(note) { saveNotes(sNotes.getAll()); }),
          resized: (function(note) { saveNotes(sNotes.getAll()); }),
          edited: (function(note) { saveNotes(sNotes.getAll()); }),
          deleted: (function(note) { saveNotes(sNotes.getAll()); })
        }
      };
      
      sNotes.init(settings);
    });
    
    function saveNotes(all_notes) {
      // saving all notes via ajax, for example
    }

Use sNotes on specific element only
===================================

It may be handy to limit using sNotes on specific page element only. It is defaultly set to tag `<body>`. To change it, you can use any element with unique attribute `ID` (use jQuery format with `#`).

It is allowed to set another options, see example below.

    jQuery(document).ready(function() {
      var settings = {
        options: {
          // sNotes works only inside #page element, include itself
          container: '#page',
          // if true, user can see notes only
          readonly: false,
          // if false, instructions panel is not displayed
          instructions: true
        }
      };
      
      sNotes.init(settings);
    });

Rendering already saved notes
=============================

You can also render notes, which was already saved with another user, for example. User also can create a few notes, close the page and continue later and thanks to this feature, no notes will be lost.

    jQuery(document).ready(function() {
      var settings = {
        notes: {
          0: {'id': 36, 'element': 462, 'date': '04.10.2014', 'width': '200', 'height': '150', 'x': '550', 'y': '356', 'text': 'Text content of this note'}
        }
      };
      
      sNotes.init(settings);
    });
