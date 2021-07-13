# tree-style-tab-modo-theme
Based on doublejim’s [tree-style-tab-compact-dark-style](https://github.com/doublejim/tree-style-tab-compact-dark-style). If this is your first time using Tree Style Tab, his respository contains a nice guide for setting it up.

<img alt="screenshot" src="https://raw.githubusercontent.com/plu5/tree-style-tab-modo-theme/master/screenshot.png"/>

Here is the theme I made based on his. To use it, paste this in <kbd>Tree Style Tab options > Advanced > Extra style rules</kbd>, and set theme to <kbd>No Decoration</kbd>.

```css
:root {
  --colorA: #eedc82; /* selected tab colour */
  --colorB: #5E686D; /* background colour */
  --tab-height: 19px;
  --font-size: 11px;
}

#background {
  background: var(--colorB);
}

/* indented area before tab */
tab-item .extra-items-container.indent {
  background-color: var(--colorB);
}

/* White X */
:root.simulate-svg-context-fill .closebox::after {
  background: white;
}

/* Closebox only on hover */
#tabbar tab-item:not(:hover) tab-closebox {
  display: none;
}

/* Move twisty a bit to the left */
.tab .twisty {
  margin-left: -2px;
}

/* Colour of twisty on active tab */
:root.simulate-svg-context-fill .tab.active .twisty::before {
  background: grey;
}

/* Colour of closebox on active tab */
:root.simulate-svg-context-fill .tab.active .closebox::after {
  background: black;
}
:root.simulate-svg-context-fill .tab.active:hover .closebox::after {
  background: black;
}

/* Colour of closebox on hover */
:root.simulate-svg-context-fill .tab:hover .closebox::after {
  background: white;
}

/* Colour of soundbutton on active tab  */
:root.simulate-svg-context-fill .tab.active .sound-button::after {
  background: black;
}
:root.simulate-svg-context-fill .tab.active:hover .sound-button::after {
  background: black;
}

/* Colour of soundbutton on hover */
:root.simulate-svg-context-fill .tab:hover .sound-button::after {
  background: white;
}


.tab {
  height: var(--tab-height);
  border: none;
  background: var(--colorB);
}

.label {
  font-size: var(--font-size);
  margin-top: -2px;
  margin-left: 2px;
  color: white;
  line-height: var(--tab-height);
}
.tab .label {
  color: white;
}
.tab.active .label {
  color: black;
}

/* Style of the label that shows number of tabs (#) on collapsed trees */
.tab .counter {
  color: #F63737;
}

.tab.active {
  color: black;
  background-color: var(--colorA);
  border-left: solid;
}
.tab.active:hover {
  background-color: var(--colorA);
}

/* Styling of unread tabs */
.tab.unread .label {
  font-style: italic;
}

/* Styling of pending (unloaded) tabs */
.tab.discarded {
  opacity: 0.75;
  font-style: italic;
}

/* Add private browsing indicator per tab */
.tab.private-browsing .label:before {content: "🕶 ";}


/* ----- Tab counter ----- */
#tabbar {
  counter-reset: vtabs atabs tabs;
  /* vtabs tracks visible tabs, atabs tracks active tabs, tabs tracks all tabs */
}
tab-item:not(.collapsed):not(.discarded) {
  counter-increment: vtabs atabs tabs;
}
tab-item:not(.collapsed) {
  counter-increment: vtabs tabs;
}
tab-item:not(.discarded) {
  counter-increment: atabs tabs;
}
tab-item {
  counter-increment: tabs;
}
.newtab-button::before {
  color: white;
  content: var(--tab-count-text);
  pointer-events: none;
    
  position: absolute;
  left: 0.5em;
}
.newtab-button {
  --tab-count-text: counter(tabs) " tabs";
  margin-top: 2px;
  font-size: 11px;
  border-top: solid 1px rgba(255, 255, 255, .4);
  border-bottom: solid 1px rgba(255, 255, 255, .4);
}
:root.simulate-svg-context-fill .newtab-button::after {
  background: white;
  width: 13px;
  height: 12px;
  margin-top: 1px;
}


/* ----- Specific domains ----- */
tab-item[data-current-uri^="https://github.com"] {
  background-color: #5E736D;
}
tab-item[data-current-uri^="https://www.youtube.com"] {
  background-color: #71686D;
}
tab-item[data-current-uri^="https://www.google"] {
  background-color: #828282;
}
tab-item[data-current-uri^="https://twitter.com"] {
  background-color: #5E788C;
}
tab-item[data-current-uri^="about:"] {
  background-color: #726558;
}
```
