# Smartboards

Smartboards is an interactive networked public noticeboard framework. It was developed to facilitate remote communication between members of the [Cambridge Computer Lab](http://www.cl.cam.ac.uk/)'s [Graphics and Interaction](http://www.cl.cam.ac.uk/research/rainbow/) research group.

The system was designed for large touch-screen displays located along the research group's corridor, each powered by a [Raspberry Pi](http://www.raspberrypi.org/). Members can also view and edit the boards remotely via web-apps, keeping the group updated on their status or interests.

![Image of kiosk in use](http://i.imgur.com/tJ97xoL.jpg)

It is comprised of three web-app interfaces:

1. The **kiosk** - an optimized editor designed for public terminal use with a kiosk-mode browser
2. The **editor** - a more feature-rich editor for desktop or mobile use
3. The **viewer** - a responsive smartboard browser and settings editor.

## Content structure

Each office (or room) has an external smartboard, shared by that office's users. The smartboard display is split vertically into several *panes*, one for each user. Each pane consists of a profile picture and description of its user, and a large section displaying a [SVG](http://www.w3.org/Graphics/SVG/).

The SVG consists of images that can be moved around or resized. These either link externally or include the image in-line using a [data URI](https://developer.mozilla.org/en/docs/data_URIs). Users also have the option to embed a website behind the SVG which may be interactive.

Rooms have a unique id of the form `r_ROOM_ID`, e.g. `r_01`. Each room's smartboard is determined by a configuration `/config/room/r_ROOM_ID.xml` which describes a list of users with panes. Users have ids of the form `u_USER_ID`, and an associated SVG `content/u_USER_ID.svg`. They may also have a profile pic `images/profile-pic/u_USER_ID.jpg`

## Kiosk

The kiosk editor is available for a particular room at `/kiosk.html?r_id=r_ROOM_ID`.

Users can draw bitmaps on a *simulated whiteboard* to place within the SVG, and move and delete current SVG elements. Users can also interact with any embedded background webpages.

## Editor

The full editor is available for a particular room at `/editor.html?r_id=r_ROOM_ID`.

As well as drawing with a simulated whiteboard, users can also add linked images and generate QR codes of URLs or text.

A mobile-centric option for writing a quick status update will be added soon.

## Viewer

The viewer is available at `/viewer.html`.

It shows a list of all rooms found in the `/config/room/` directory. Users can modify each room's settings.

## Dependencies

* [jQuery](http://jquery.com/) - a multi-purpose javascript library
* [jQuery.qrcode.js](http://jeromeetienne.github.io/jquery-qrcode/) - allows the editor to generate QR codes in-browser
* [jQuery.ScrollTo](http://demos.flesler.com/jquery/scrollTo/) - for scrolling between views in the web-app's mobile configuration 
