---
layout: post
title:  "Passwordless cups"
author: "rusty-snake"
#tags:
---

Annoyed by entering your password every time you change printer settings in
gnome-control-center?

Create `/etc/polkit-1/rules.d/40-passwordless-cups.rules`:

~~~ js
polkit.addRule(function(action, subject) {
    if (action.id == "org.opensuse.cupspkhelper.mechanism.all-edit" &&
        subject.isInGroup("wheel")) {
        return polkit.Result.YES;
    }
});
~~~
