<!-- Changelog -->
# Changelog

## v1.3.1

### Added or Changed
- Completely new and robust logic for syncing changes

         - Can sync changes even when done with GUI and CLI, by any process
         - Leaves no dangling process.
- Support for automatically starting the monitoring process on login
- Elaborative and colorful logs in a separate log-file, cleared on every login
- Super convenient logs and process/service management
- Service management is more binocular, supports starting and stopping of individual processes specified by user
- Also included `enable` and `disable` modes for services
- fixed excess battery drain issue in v1.3

### Removed

- `-a` argument. No need for any alias now, edit however you want
- Old one way method of editing and syncing files
- Shell dependency
