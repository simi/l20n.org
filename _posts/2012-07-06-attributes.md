---
category: learn
layout: learn
title: Attributes
prev_section: indexes-for-hash-tables
next_section: context-data
---

Attributes can be used to store additional information about entities.

While entity values discussed in previous chapters store the representation of the entity to be displayed in the UI, it is sometimes useful to describe the entity with some meta-data:
 - grammar meta-data, such as gender, animate vs. inanimate etc.
 - UI meta-data, such as tooltips, accesskeys, keyboard shortcuts etc.

Attributes come after the entity value and are defined with a colon, followed by the name of the attribute.  You can reference attributes from other parts of the L20n code with the double-colon (`::`) syntax.

<div id="editor1" class="editor height15">&lt;follow "Follow"
 accesskey: "F"
&gt;
&lt;unfollow "Unfollow"
 accesskey: "U"
&gt;
&lt;followHelp "To follow someone, press Ctrl+{% raw %}{{ follow::accesskey }}{% endraw %}"&gt;
&lt;unfollowHelp "To unfollow someone, press Ctrl+{% raw %}{{ unfollow::['accesskey'] }}{% endraw %}"&gt;
</div>
<dl id="output">
</dl>

Attribute values follow the exact same rules as entity values do:  they can be strings or dictionaries (also nested ones), and can define indexes and default values.

<div id="editor2" class="editor height25">&lt;settings {
 *win: "Settings",
  mac: "Preferences"
 }
 accesskey: {
  *win: "S",
   mac: "P"
 }
&gt;
&lt;helpWin "To open Settings, press Ctrl+{% raw %}{{ settings::accesskey }}{% endraw %}"&gt;
&lt;helpMac "To open Preferencds, press Cmd+{% raw %}{{ settings::accesskey.mac }}{% endraw %}"&gt;
</div>
<dl id="output">
</dl>

(See <a href="{% post_url 2012-07-12-globals-os %}">Chapter 12. "Globals: @os"</a> for a better way of implementing this.)