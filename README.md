# FirstTestingProject
Trying out Github

#Testing to create website using github. 
Below is the reference of the youtube video.
https://www.youtube.com/watch?v=RGOj5yH7evk

Learning how to create a website, different between Git Desktop and Visual Studio Code
Visual Code to Link up with GitHub

Purpose is to help the developer community (esp the Junior Role).
As a senioer developer, sometimes we do forget a thing or two, hence, recording whatever I have learnt or practise over the period. 

ABAP Developer, Web Developer.

Website shall focus on two main topics, SAP and Website. 
1) SAP consist of SAP Process Flow and ABAP Development
2) Website consist of HTML, CSS and builind a website from scratch.  



{
    "workbench.colorTheme": "Visual Studio Light",
    "terminal.integrated.tabs.enabled": true,
    "launch": {

        "configurations": [],
        "compounds": []
    }

    {
        // OPTIONAL WORD WRAPPING
        // Controls if lines should wrap. The lines will wrap at min(editor.wrappingColumn, viewportWidthInColumns).
        "editor.wordWrap": "off",
        
        // Controls the indentation of wrapped lines. Can be one of 'none', 'same' or 'indent'.
        "editor.wrappingIndent": "none",
    
        // TURN OFF AUTOCOMPLETION
        // Controls if quick suggestions should show up or not while typing
        "editor.quickSuggestions": true,
    
        // Controls the delay in ms after which quick suggestions will show up
        "editor.quickSuggestionsDelay": 90,
    
        // Enables parameter hints
        "editor.parameterHints": false,
    
        // Controls if the editor should automatically close brackets after opening them
        "editor.autoClosingBrackets": false,
    
        // Controls if the editor should automatically format the line after typing
        "editor.formatOnType": false,
    
        // Controls if suggestions should automatically show up when typing trigger characters
        "editor.suggestOnTriggerCharacters": true,
    
        // Controls if suggestions should be accepted 'Enter' - in addition to 'Tab'. Helps to avoid ambiguity between inserting new lines or accepting suggestions.
        "editor.acceptSuggestionOnEnter": "off",

        "editor.tabCompletion": "on",
        
        "html.autoClosingTags": false,
        "html.format.enable": false,
        "html.validate.scripts": false,
        "html.suggest.html5": true,
        "html.format.extraLiners": ""
        
    }



Notes

*--------------------------------------------------------------------
*For Field ZDIS
*--------------------------------------------------------------------
  SELECTION-SCREEN BEGIN OF LINE.
  PARAMETERS: r_zdis RADIOBUTTON GROUP rg1 MODIF ID rg1.
  SELECTION-SCREEN COMMENT (6) FOR FIELD r_zdis MODIF ID rg1.
  SELECTION-SCREEN POSITION 10.
  PARAMETERS p_zdis(4) TYPE c MODIF ID rg1.
  SELECTION-SCREEN COMMENT (10) FOR FIELD p_zdis MODIF ID rg1.
  SELECTION-SCREEN COMMENT (10) FOR FIELD p_zmpl_d MODIF ID rg1.
  PARAMETERS: p_zdis_d TYPE sy-datum MODIF ID rg1.
  SELECTION-SCREEN END OF LINE.

*Selection for ZDIS Key Combination
  SELECTION-SCREEN BEGIN OF LINE.
  SELECTION-SCREEN POSITION 5.
  PARAMETERS: r_zdis01 RADIOBUTTON GROUP zdis MODIF ID dis.
  SELECTION-SCREEN COMMENT (25) FOR FIELD r_zdis01 MODIF ID dis.
  SELECTION-SCREEN POSITION 35.
  PARAMETER:  r_zdis02 RADIOBUTTON GROUP zdis MODIF ID dis.
  SELECTION-SCREEN COMMENT (30) FOR FIELD r_zdis02 MODIF ID dis.
  SELECTION-SCREEN END OF LINE.

  SELECTION-SCREEN BEGIN OF LINE.
  SELECTION-SCREEN POSITION 5.
  PARAMETERS: r_zdis03 RADIOBUTTON GROUP zdis MODIF ID dis.
  SELECTION-SCREEN COMMENT (20) FOR FIELD r_zdis03 MODIF ID dis.
  SELECTION-SCREEN POSITION 35.
  PARAMETERS: r_zdis04 RADIOBUTTON GROUP zdis MODIF ID dis.
  SELECTION-SCREEN COMMENT (30) FOR FIELD r_zdis04 MODIF ID dis.

  SELECTION-SCREEN END OF LINE.

  SELECTION-SCREEN BEGIN OF LINE.
  SELECTION-SCREEN POSITION 5.
  PARAMETERS: r_zdis05 RADIOBUTTON GROUP zdis MODIF ID dis.
  SELECTION-SCREEN COMMENT (25) FOR FIELD r_zdis05 MODIF ID dis.
  SELECTION-SCREEN POSITION 35.
  PARAMETERS: r_zdis06 RADIOBUTTON GROUP zdis MODIF ID dis DEFAULT 'X'.
  SELECTION-SCREEN COMMENT (30) FOR FIELD r_zdis06 MODIF ID dis.
  SELECTION-SCREEN END OF LINE.

  SELECTION-SCREEN SKIP.

*--------------------------------------------------------------------
*For Selection Screen Download File
*--------------------------------------------------------------------

*Blocks for user using excel as inputs for sales number
  PARAMETERS: x_file AS CHECKBOX DEFAULT space.
  PARAMETERS: p_file TYPE string.
  SELECTION-SCREEN COMMENT /1(79) text002.
  SELECTION-SCREEN END OF BLOCK a1.

*--------------------------------------------------------------------
*For Selection Screen ZVSL03
*--------------------------------------------------------------------

  SELECTION-SCREEN BEGIN OF BLOCK b1 WITH FRAME TITLE text-002.
  PARAMETERS: p_vkorg TYPE tvko-vkorg  DEFAULT '1010' OBLIGATORY,
              p_werks TYPE t001w-werks DEFAULT '1010' OBLIGATORY.

  SELECT-OPTIONS: s_matnr FOR mvke-matnr.
  PARAMETERS:     p_kunnr TYPE knvv-kunnr.
  SELECT-OPTIONS: s_prdha FOR mara-prdha.
  PARAMETERS:     p_lgort TYPE mard-lgort.
  SELECT-OPTIONS: s_matkl FOR mara-matkl.

  PARAMETERS:     p_date TYPE datum   DEFAULT sy-datum,
                  p_waers TYPE waers  DEFAULT 'SGD'  OBLIGATORY,
                  p_inco  TYPE inco1.
  SELECTION-SCREEN END OF BLOCK b1.

*&---------------------------------------------------------------------*
*& AT SELECTION-SCREEN
*&---------------------------------------------------------------------*
AT SELECTION-SCREEN.

*IF radiobutton is changed, below validation should not be checked,
*only when "Enter" key is clicked or F8
  IF sy-ucomm EQ 'RGA'.
    CLEAR sy-ucomm.
    EXIT.
  ENDIF.

  IF r_act01 EQ abap_true.
*Validation on the Mandatory field depending on the Condition Selected.
    IF r_zmpl EQ abap_true.
      IF p_zmpl IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter % change for ZMPL'.
      ENDIF.
      IF p_zmpl_d IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter date for ZMPL'.
      ENDIF.
    ENDIF.

    IF r_zmul EQ abap_true.
      IF p_zmul IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter a value for ZMUL'.
      ENDIF.
      IF p_zmul_d IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter date for ZMUL'.
      ENDIF.
    ENDIF.

    IF r_zexc EQ abap_true.
      IF p_zexc IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter a value for ZEX1'.
      ENDIF.
      IF p_zexc_d IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter date for ZEX1'.
      ENDIF.
    ENDIF.

    IF r_zfrt EQ abap_true.
      IF p_zfrt IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter a value for ZFRT'.
      ENDIF.
      IF p_zfrt_d IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter date for ZFRT'.
      ENDIF.
    ENDIF.

    IF r_zfct EQ abap_true.
      IF p_zfct IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter a value for ZFCT'.
      ENDIF.
      IF p_zfct_d IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter date for ZFCT'.
      ENDIF.
    ENDIF.

    IF r_zbuf EQ abap_true.
      IF p_zbuf IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter a value for ZBUF'.
      ENDIF.
      IF p_zbuf_d IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter date for ZBUF'.
      ENDIF.
    ENDIF.

    IF r_zdis EQ abap_true.
      IF p_zdis IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter a value for ZDIS'.
      ENDIF.
      IF p_zdis_d IS INITIAL.
        MESSAGE e000(zc903) WITH 'Please enter date for ZDIS'.
      ENDIF.
    ENDIF.
  ENDIF.

  IF x_file EQ abap_true
    AND p_file IS INITIAL.
    MESSAGE e000(zc903) WITH 'Please enter the folder path'.
  ENDIF.

*&---------------------------------------------------------------------*
*& AT SELECTION-SCREEN OUTPUT
*&---------------------------------------------------------------------*
AT SELECTION-SCREEN OUTPUT.
*  text001 = 'Select one of the brand'.
  text002 = 'A folder shall be created for the result generated'.
  text003 = 'Select at least one field below (for decrease include "-" infront)'.
  texth001 = 'Price markup based on'.

*Selection Screen, hide all the unnecessary fields
  PERFORM hide_screen.

AT SELECTION-SCREEN ON VALUE-REQUEST FOR p_file.

  CALL METHOD cl_gui_frontend_services=>directory_browse
    CHANGING
      selected_folder      = p_file
    EXCEPTIONS
      cntl_error           = 1
      error_no_gui         = 2
      not_supported_by_gui = 3
      OTHERS               = 4.



----------------------------------------------------------
Website
1. Color Hunt 
2. Flat UI color
3. Material Palette
4. UX Pin
5. Icon Stone
6. Reverse Dictionary






