# Labs features

If Labs is enabled in the [Element config](config.md), you can enable some of these features by going
to `Settings->Labs`. This list is non-exhaustive and subject to change, chat in
[#element-web:matrix.org](https://matrix.to/#/#element-web:matrix.org) for more information.

**Be warned! Labs features are not finalised, they may be fragile, they may change, they may be
dropped. Ask in the room if you are unclear about any details here.**

## Submit Abuse Report to Moderators [MSC3215](https://github.com/matrix-org/matrix-doc/pull/3215) support (`feature_report_to_moderators`)

A new version of the "Report" dialog that lets users send abuse reports directly to room moderators,
if the room supports it.

## Render LaTeX maths in messages (`feature_latex_maths`)

Enables rendering of LaTeX maths in messages using [KaTeX](https://katex.org/). LaTeX between single dollar-signs is interpreted as inline maths and double dollar-signs as display maths (i.e. centred on its own line).

## Message pinning (`feature_pinning`)

Allows you to pin messages in the room. To pin a message, use the 3 dots to the right of the message
and select "Pin".

## Custom status (`feature_custom_status`)

An experimental approach for supporting custom status messages across DMs. To set a status, click on
your avatar next to the message composer.

## Custom tags (`feature_custom_tags`)

An experimental approach for dealing with custom tags. Custom tags will appear in the bottom portion
of the community filter panel.

Setting custom tags is not supported by Element.

## Render simple counters in room header (`feature_state_counters`)

Allows rendering of labelled counters above the message list.

Once enabled, send a custom state event to a room to set values:

1. In a room, type `/devtools` to bring up the devtools interface
2. Click "Send Custom Event"
3. Toggle from "Event" to "State Event"
4. Set the event type to: `re.jki.counter` and give it a unique key
5. Specify the content in the following format:

```
{
    "link": "",
    "severity": "normal",
    "title": "my counter",
    "value": 0
}
```

That's it. Now should see your new counter under the header.

## Multiple integration managers (`feature_many_integration_managers`)

Exposes a way to access all the integration managers known to Element. This is an implementation of [MSC1957](https://github.com/matrix-org/matrix-doc/pull/1957).

## New ways to ignore people (`feature_mjolnir`)

When enabled, a new settings tab appears for users to be able to manage their ban lists.
This is a different kind of ignoring where the ignored user's messages still get rendered,
but are hidden by default.

Ban lists are rooms within Matrix, proposed as [MSC2313](https://github.com/matrix-org/matrix-doc/pull/2313).
[Mjolnir](https://github.com/matrix-org/mjolnir) is a set of moderation tools which support
ban lists.

## Verifications in DMs (`feature_dm_verification`)

An implementation of [MSC2241](https://github.com/matrix-org/matrix-doc/pull/2241). When enabled, verification might not work with devices which don't support MSC2241.

This also includes a new implementation of the user & member info panel, designed to share more code between showing community members & room members. Built on top of this new panel is also a new UX for verification from the member panel.

The setting will be removed in a future release, enabling it non-optionally for
all users.

## Bridge info tab (`feature_bridge_state`)

Adds a "Bridge Info" tab to the Room Settings dialog, if a compatible bridge is
present in the room. The Bridge info tab pulls information from the `m.bridge` state event ([MSC2346](https://github.com/matrix-org/matrix-doc/pull/2346)). Since the feature is based upon a MSC, most
bridges are not expected to be compatible, and users should not rely on this
tab as the single source of truth just yet.

## Presence indicator in room list (`feature_presence_in_room_list`)

This adds a presence indicator in the room list next to DM rooms where the other
person is online.

## Custom themes (`feature_custom_themes`)

Custom themes are possible through Element's [theme support](./theming.md), though
normally these themes need to be defined in the config for Element. This labs flag
adds an ability for end users to add themes themselves by using a URL to the JSON
theme definition.

For some sample themes, check out [aaronraimist/element-themes](https://github.com/aaronraimist/element-themes).

## Message preview tweaks

To enable message previews for reactions in all rooms, enable `feature_roomlist_preview_reactions_all`.
To enable message previews for reactions in DMs, enable `feature_roomlist_preview_reactions_dms`, ignored when it is enabled for all rooms.

## Communities v2 prototyping (`feature_communities_v2_prototypes`) [In Development]

**This is a highly experimental implementation for parts of the communities v2 experience.** It does not
represent what communities v2 will look/feel like and can/will change without notice. Due to the early
stages this feature is in and the requirement for a compatible homeserver, we will not be accepting issues
or feedback for this functionality at this time.

## Dehydrated devices (`feature_dehydration`)

Allows users to receive encrypted messages by creating a device that is stored
encrypted on the server, as described in [MSC2697](https://github.com/matrix-org/matrix-doc/pull/2697).

## Do not disturb (`feature_dnd`)

Enables UI for turning on "do not disturb" mode for the current device. When DND mode is engaged, popups
and notification noises are suppressed. Not perfect, but can help reduce noise.

## Hidden read receipts (`feature_hidden_read_receipts`)

Enables sending hidden read receipts as per [MSC2285](https://github.com/matrix-org/matrix-doc/pull/2285)

## New layout switcher (with message bubbles) (`feature_new_layout_switcher`)

Adds a "Message layout" section under `Settings -> Appearance`, where the user can select their preferred message layout (e.g. IRC or Modern). Additionally, adds a new "Message bubbles" layout.

## Polls (`feature_polls`) [In Development]

Polls are a way to gauge interest from your community about a certain topic with a simple voting mechanic
within the message timeline. Note that this feature is currently under active development and therefore is
entirely incomplete and may not work at all - it is not recommended for general use at this time.

Bug reports, feature requests, etc are not currently accepted for this feature flag. A later stage of
development will provide opportunities for feedback.

## Metaspaces (`feature_spaces_metaspaces`) [In Development]

Metaspaces are automatically populated spaces you can enable in your Space panel.
By default, you'll have Home or All rooms, but you can opt in to a People, Favourites, and Other Rooms metaspace too.

## Location sharing (`feature_location_share`) [In Development]

Allows users to send and display location data using [maplibre](https://maplibre.org).

The current implementation is a quick in-progress development spike to
demonstrate viability and prove [MSC3488](https://github.com/matrix-org/matrix-doc/pull/3488)
and [MSC3489](https://github.com/matrix-org/matrix-doc/pull/3489) - **the UI has not yet
been designed, and it will not exit labs until it has**.

For this to work, you must specify a valid maptiler.com API key in
`"map_style_url": "https://api.maptiler.com/maps/basic/style.json?key=YOUR_KEY_GOES_HERE"`
in your config.json, or find an alternative map tile server.

## Breadcrumbs v2 (`feature_breadcrumbs_v2`)

Instead of showing the horizontal list of breadcrumbs under the filter field, the new UX is an interactive context menu
triggered by the button to the right of the filter field.

## Spotlight search (`feature_spotlight`) [In Development]

Switches to a new room search experience.
