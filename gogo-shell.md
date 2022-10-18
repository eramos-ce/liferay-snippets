# GoGo Shell Useful Commands

## Commands for troubleshooting

1. `diag`   - runs a diagnostic and checks for issues starting deployed bundles.
2. `dm wtf` - another diagnostic check.  Verifies dependencies.
3. `system:check` - runs a series of verifications.
4. `lb` - Lists all bundles on your deployment.
5. `lb <text>` - Lists all bundles on your deployment whose name matches the input text.  Think grep.
6. `bundle <bundle id>` - Prints many details about a given bundle.  Important to note here are the list of referenced services as well as the list of provided services. If you expect a service to be provided but it's not on the list, there's almost certainly an issue wiring all of it's dependencies.
7. `scr:list` & `scr:info` - Prints all services and components that have been correctly wired.
