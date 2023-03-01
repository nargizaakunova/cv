<a name="16.0.0-next.0"></a>
# 16.0.0-next.0 (2023-02-22)
## Breaking Changes
### compiler
- Angular Compatibility Compiler (ngcc) has been removed. As a result, Angular View Engine libraries can no longer be used in v16+. Such libraries were not officially supported, but this is a hard break in compatibility.
### common
- `MockPlatformLocation` is now provided by default in tests.
  Existing tests may have behaviors which rely on
  `BrowserPlatformLocation` instead. For example, direct access to the
  `window.history` in either the test or the component rather than going
  through the Angular APIs (`Location.getState()`). The quickest fix is to
  update the providers in the test suite to override the provider again
  `TestBed.configureTestingModule({providers: [{provide: PlatformLocation, useClass: BrowserPlatformLocation}]})`.
  The ideal fix would be to update the code to instead be compatible with
  `MockPlatformLocation` instead.
### core
- `RendererType2.styles` no longer accepts a nested arrays.
### router
- The `Scroll` event's `routerEvent` property may also be
  a `NavigationSkipped` event. Previously, it was only a `NavigationEnd`
  event.
- The `RouterEvent` type is no longer present in the `Event` union type representing all router event types. If you have code using something like `filter((e: Event): e is RouterEvent => e instanceof RouterEvent)`, you'll need to update it to `filter((e: Event|RouterEvent): e is RouterEvent => e instanceof RouterEvent)`.
### 
| Commit | Type | Description |
| -- | -- | -- |
| [48aa96ea13](https://github.com/angular/angular/commit/48aa96ea13ebfadf2f6b13516c7702dae740a7be) | refactor | remove Angular Compatibility Compiler (ngcc) ([#49101](https://github.com/angular/angular/pull/49101)) |
### common
| Commit | Type | Description |
| -- | -- | -- |
| [5dce2a5a3a](https://github.com/angular/angular/commit/5dce2a5a3a00693d835a57934b9abacce5a33dfa) | feat | Provide MockPlatformLocation by default in BrowserTestingModule ([#49137](https://github.com/angular/angular/pull/49137)) |
### core
| Commit | Type | Description |
| -- | -- | -- |
| [bc5ddabdcb](https://github.com/angular/angular/commit/bc5ddabdcb39e6ebbe2da03dc8ec49bbe26c677d) | feat | add Angular Signals to the public API ([#49150](https://github.com/angular/angular/pull/49150)) |
| [9b9c818f99](https://github.com/angular/angular/commit/9b9c818f99c44473e915bedd157146c88e44989a) | perf | change `RendererType2.styles` to accept a only a flat array ([#49072](https://github.com/angular/angular/pull/49072)) |
### router
| Commit | Type | Description |
| -- | -- | -- |
| [1f055b90b6](https://github.com/angular/angular/commit/1f055b90b65cce2d0d063ed44cb0f8fbecb9b1f6) | fix | Ensure anchor scrolling happens on ignored same URL navigations ([#48025](https://github.com/angular/angular/pull/48025)) |
| [1e32709e0e](https://github.com/angular/angular/commit/1e32709e0e16f553ed3e7778705c9a0c5641d0af) | fix | remove RouterEvent from Event union type ([#46061](https://github.com/angular/angular/pull/46061)) |
## Special Thanks
Alan Agius, Alex Rickabaugh, Andrew Kushnir, Andrew Scott, Cédric Exbrayat, Joey Perrott, Mladen Jakovljević and Pawel Kozlowski

<!-- CHANGELOG SPLIT MARKER -->
