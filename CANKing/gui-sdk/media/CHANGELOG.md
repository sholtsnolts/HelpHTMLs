# Changelog

All notable changes to `@kvaser/canking-api` are documented in this file.

The SDK version follows the CanKing application version. Version increments are therefore tied to application releases
instead of strict SemVer bump rules based on breaking vs non-breaking API changes.

## [7.5.0] - 2026-05-29

### Breaking changes

#### `@kvaser/canking-api/controls`

- **Removed:** `useMessageDatabases` and `IMessageDatabase` were moved from`@kvaser/canking-api/controls` to `@kvaser/canking-api/hooks`.
- **Changed:** `ToolbarControl` no longer wraps items onto a new line when they overflow. Items that do not fit are now collapsed into an overflow menu (ellipsis button). Toolbars that relied on the previous multi-line wrapping behavior will need to adjust their layout.

#### `@kvaser/canking-api/hooks`

- **Changed:** `useOnlineStatus` changed signature and now returns `IOnlineStatusContext`. The hook now exposes `onlineStatus`, `isLoaded`, and `error` as one object instead of returning only the online status payload.
- **Added:** `useMessageDatabases` and `IMessageDatabase` were moved from`@kvaser/canking-api/controls` to `@kvaser/canking-api/hooks`.

#### `@kvaser/canking-api/models`

- **Removed:** `Frame.time` has been removed, use `Frame.timeUs` instead.
- **Removed:** `ApiPreferences` type and all related exports. API preferences (`version`, `language`,
               `useHexNumericBase`, `username`, `apiVersion`) are now conveyed via gRPC metadata and
               are no longer part of the proto message API.

### Non-breaking changes

#### `@kvaser/canking-api/controls`

- **Added:** `DividerItemProps` - new exported interface for configuring toolbar dividers.
- **Added:** `toolbarItem.divider` - new optional `divider` field on `toolbarItem` for inserting horizontal/vertical dividers into `ToolbarControl`.
- **Added:** `DropdownButtonProps.fullWidth` - new optional boolean prop to stretch a `DropdownButton` to its container width.
- **Added:** `ButtonProps.fullWidth` - new optional boolean prop on the toolbar's `ButtonProps` to stretch a button to available width.

#### `@kvaser/canking-api/hooks`

- **Added:** `useMeasurementSetupState`.
- **Added:** `useMeasurementStatusState`.
- **Added:** `useCombinedMeasurementTraceData`.

### Migration

- Update `useOnlineStatus` usage:

```tsx
// Before
const onlineStatus = useOnlineStatus();
const isOnline = onlineStatus?.isOnline === true;

// After
const { onlineStatus, isLoaded, error } = useOnlineStatus();
const isOnline = onlineStatus?.isOnline === true;
```

- Update `useMessageDatabases` and `IMessageDatabase` imports:

```tsx
// Before
import { useMessageDatabases, IMessageDatabase } from '@kvaser/canking-api/controls';

// After
import { useMessageDatabases, IMessageDatabase } from '@kvaser/canking-api/hooks';
```

- Use `Frame.timeUs` instead of `Frame.time`:

```tsx
// Before
const timeInSeconds = frame.time;

// After
const timeInSeconds = frame.timeUs.toNumber() / 1_000_000;
```

## [7.4.0] - 2026-02-27

- Initial public release of `@kvaser/canking-api`.
