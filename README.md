Backbone.GoogleMaps
===================

A Backbone JS extension for interacting with the Google Maps API (v3.10)

## About backbone.googlemaps

Backbone.GoogleMaps is a simple Backbone JS extension for simplified interactions with the Google Maps API. The motivation for creating this extension was to have an easy way to sync data about maps locations from a database with the Google Maps UI, using Backbone's RESTful interface.

## Example

```javascript  	
// Create Google map instance
var places = new Backbone.GoogleMaps.LocationCollection([
	{
		title: "Walker Art Center",
		lat: 44.9796635,
		lng: -93.2748776
	},
	{
		title: "Science Museum of Minnesota",
		lat: 44.9429618,
		lng: -93.0981016
	}
];

var map = new google.maps.Map($('#map_canvas')[0], {
	center: new google.maps.LatLng(44.9796635, -93.2748776),
	zoom: 12,
	mapTypeId: google.maps.MapTypeId.ROADMAP
});

// Render Markers
var markerCollectionView = new Backbone.GoogleMaps.MarkerCollectionView({
	collection: places,
	map: map
});
markerCollectionView.render();
```

## Backbone.GoogleMaps Components

Backbone.GoogleMaps is packaged with several customizable components.

### GoogleMaps.Location
Represents a lat/lng location on a map. Extends Backbone.Model.

#### Properties
<table>
	<tr>
		<td>Property</td><td>Default Value</td><td>Description</td>
	</tr>
	<tr>
		<td>lat</td>
		<td>0</td>
		<td>The location's latitude</td>
	</tr>
	<tr>
		<td>lng</td>
		<td>0</td>
		<td>The location's longitute</td>
	</tr>
	<tr>
		<td>selected</td>
		<td>false</td>
		<td>A flag for selecting a location/<td>
	</tr>
	<tr>
		<td>title</td>
		<td>""</td>
		<td>Location title</td>
	</tr>
</table>

#### Methods
<table>
	<tr>
		<td>Method</td>
		<td>Parameters</td>
		<td>Return Value</td>
		<td>Description</td>
	</tr>
	<tr>
		<td>select</td>
		<td>none</td>
		<td>none</td>
		<td>Sets the model's selected property as true. Triggers a "selected" event on the model.</td>
	</tr>
	<tr>
		<td>deselect</td>
		<td>none</td>
		<td>none</td>
		<td>Sets the model's selected property as false. Triggers a "deselected" event on the model.</td>
	</tr>
	<tr>
		<td>toggleSelect</td>
		<td>none</td>
		<td>none</td>
		<td>Toggles the model's selected property.</td>
	</tr>
	<tr>
		<td>getLatLng</td>
		<td>none</td>
		<td>google.maps.LatLng instance</td>
		<td>Returns the latitude and longitude of the model</td>
	</tr>
</table>

## GoogleMaps.LocationCollection

A collection of GoogleMaps.Location objects. Extends Backbone.Collection.

Only a single `Location` model can be selected in a given `LocationCollection` at any time.

## GoogleMaps.MapView

A generic GoogleMaps view, for controlling an maps overlay instance. Extends Backbone.View.

### Constructor Options

<table>
	<tr>
		<td>mapEvents</td>
		<td>{}</td>
		<td>Hash of Google Map events. Events are attached to this.gOverlay (google map or overlay)</td>
	</tr>
	<tr>
		<td>map</td>
		<td>none</td>
		<td>The google.maps.Map instance to which the overlay is attached</td>
	</tr>
</table>

#### Properties
<table>
	<tr>
		<td>Property</td>
		<td>Default Value</td>
		<td>Description</td>
	</tr>
	<tr>
		<td>mapEvents</td>
		<td>{}</td>
		<td>Hash of Google Map events. Events are attached to this.gOverlay (google map or overlay)</td>
	</tr>
	<tr>
		<td>gOverlay</td>
		<td>this.map</td>
		<td>The overlay instance controlled by this view</td>
	</tr>
</table>

### Methods
<table>
	<tr>
		<td>Method</td>
		<td>Parameters</td>
		<td>Return Value</td>
		<td>Description</td>
	</tr>
	<tr>
		<td>bindMapEvents</td>
		<td>mapEvents (optional)</td>
		<td>none</td>
		<td>Attaches listeners for the events in the mapEvents hash to this.gOverlay</td>
	</tr>
</table>


## GoogleMaps.InfoWindow

View controller for a google.maps.InfoWindow overlay instance. Extends `GoogleMaps.MapView`.


## GoogleMaps.MarkerView

View controller for a marker overlay. Extends `GoogleMaps.MapView`.


## GoogleMaps.MarkerCollectionView

View controller for a collection of `GoogleMaps.MarkerView` instances.



