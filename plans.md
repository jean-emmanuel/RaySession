# RaySession plans

Of course, the main objectives of RaySession are already achieved. There are still a lot of features ideas for the patchbay, see https://github.com/Houston4444/HoustonPatchbay/blob/main/plans.md. But few features can be added to RaySession itself too.

## Client <=> Patchbay box parrallel selection

Pure GUI feature, select a client on left panel also selects a matching box in the patchbay, (re-click selects another one if any). Click on a client box in the patchbay also selects the client frame in the left panel.

## Settings dialog

It's quite strange that RaySession does not have preferences dialog, we could move the systray preferences, add a checkbox for startup dialog, probably many things.

## Add some widgets to the tool bar

Since tool bar is customizable, we could add optional actions for _recents sessions_, _session scripts_, maybe others.

## Remove totally ray-proxy

RayHack does the job ray-proxy was doing. RayHack appeared in the v0.9.0 (Jul 2020). ray-proxy is still included to ensure compatibility with sessions created with older versions, but its code has not been maintained, and errors could appears because of a lib or python update. The solution could simply be to convert ray-proxy to RayHack at session open, this means it will not be possible to re-open this session with older RS version, but I didn't really care about this scenario from the start TBH, these kinds of considerations slow down development considerably.

This would be a good task for the 1.0.0 release.

## add dialog for icon selection

In client properties dialog, it would be nice to can select an icon directly, Unfortunately Qt does not provides an icon chooser, but KDE does with kdialog, it would be nice for KDE users to add a button to browse the icons with kdialog --geticon.

## improve donations dialog with tips

Give some user tips in donations dialog, make it prettier.

## list Ardour templates as RS applications

look into ~/.config/ardourX/templates and add an RS template per ardour template. This template should copy the ardour template to the RS session directory (and make the needed modifications) before to start ardour. The main problematic is with ardour versions (sometimes ardour executable is ardour, ardour7, Ardour7, etc...)

## Select a ClientId in Application Dialog

Maybe at bottom left, add a field for application to launch with specific client_id. If any, it will launch the app with long jack naming (__Application.client_id__ instead of __Application__). Useful if user uses many instances of the same software.

## Connections

ray-jackpatch could be rewritten from scratch, it uses Qt and it is clearly not needed.

Allow some automatic disconnections, sometimes some programs auto-connect some ports and it can be annoying. Of course user can set JACK settings to prevent that, but it can be boring for other softwares.

Something to see is, what to do with connections out from NSM clients at session switch? Currently it does nothing, keeping all existing connections. But if the user makes for its current session some hardware to hardware connections, theses connections won't be removed at session switch. Obviously, we can't decide to remove them when ray-jackpatch is started, it would remove (for example) PulseAudio bridges connections.

This problematic does not exists with regular NSM clients, because they remove and re-add their JACK clients (and may rename them).

## Pipewire config script

Such as Jack Config Memory script, it would be useful to can switch pipewire configs between sessions. For the moment, I don't know enough Pipewire, and another one than me could do that.

## Rooms

As carla-patchbay, be able to load inside a session, a session starting a new JACK instance (or PW if possible), with audio and midi ports. I don't know if it is really doable without extra latency.