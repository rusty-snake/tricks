---
layout: post
title:  "Passwordless cups"
author: "rusty-snake"
#tags:
---

Frustrated by having to enter your password each time you modify printer settings in
gnome-control-center?

Then allow users in the `wheel` group to do so without password prompt by creating
`/etc/polkit-1/rules.d/40-passwordless-cups.rules` with this content:

~~~ js
polkit.addRule(function(action, subject) {
    if (action.id == "org.opensuse.cupspkhelper.mechanism.all-edit" &&
        subject.isInGroup("wheel")) {
        return polkit.Result.YES;
    }
});
~~~
