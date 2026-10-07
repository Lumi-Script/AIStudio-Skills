---
name: "google-maps-platform-ghp-integration"
description: >
  Architecture and implementation for Google Maps Platform APIs and SDKs across Web, Android, and iOS.
---

# Google Maps Platform Main Skill

Governance for Google Maps Platform development in AI Studio.

## Modern API Replacements
- Marker → AdvancedMarkerElement
- PlacesService / Autocomplete → PlaceAutocompleteElement / Places API (New)
- DirectionsService → Routes API (Route.computeRoutes)
- Geocoder class → Geocoding REST API

## Technical Standards
- React: @vis.gl/react-google-maps
- Usage Attribution: internalUsageAttributionIds={["gmp_mcp_codeassist_v1_aistudio"]}
- Quota handling: two-tier in-app quota defense for demo keys.
