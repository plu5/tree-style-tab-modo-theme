# tree-style-tab-modo-theme
Based on doublejim’s [tree-style-tab-compact-dark-style](https://github.com/doublejim/tree-style-tab-compact-dark-style). If this is your first time using Tree Style Tab, his respository contains a nice guide for setting it up.

<img alt="screenshot" src="https://raw.githubusercontent.com/plu5/tree-style-tab-modo-theme/master/screenshot.png"/>

Here is the theme I made based on his. To use it, paste this in <kbd>Tree Style Tab options > Advanced > Extra style rules</kbd>.

```css
:root {
  --colorA: #eedc82; /* selected tab colour */
  --colorB: #5E686D; /* background colour */
  --tab-height: 21px;
  --font-size: 11px;
}

#background {
  background: var(--colorB);
}

/* Move X a bit to the right */
tab-closebox::after {
  margin-right: -6px;
}

/* Closebox only on hover */
#tabbar tab-item:not(:hover) tab-closebox {
  display: none;
}

/* Move twisty a bit to the left */
.tab .twisty {
  margin-left: -5px;
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

/* ----- Tab counting ----- */
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
/* Add count near new tab button */
.newtab-button::after {
  content: var(--tab-count-text);
  pointer-events: none;
    
  position: absolute;
  left: 0.5em;
  margin-top: 2px;

  /* TST 2.4.0 - Fix for Issue #1664 */
  background: transparent !important;
  mask: none !important;
}
.newtab-button {
  --tab-count-text: counter(tabs) " tabs";
  margin-top: 2px;
  font-size: 11px;
  background: var(--colorB) !important;
}
/* Smaller + on new tab button */
.newtab-button:before {
  width:13px;
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
