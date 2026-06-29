[**Kvaser CanKing GUI Extensions SDK v7.5.0**](../README.md)

***

[Kvaser CanKing GUI Extensions SDK](../modules.md) / hooks

# hooks

This module includes React hooks for getting/setting data from/to CanKing.

To be able to use these hooks the CanKingDataProvider component must be present in the
component tree above your component. Normally the CanKingDataProvider is added
at the root of the component tree.

## Example

```
import { useUserSettings } from '@kvaser/canking-api/hooks';
...
const userSettings = useUserSettings();
```

## Interfaces

- [IDevicesContext](interfaces/IDevicesContext.md)
- [IEnvelopeView](interfaces/IEnvelopeView.md)
- [IMeasurementSetupContext](interfaces/IMeasurementSetupContext.md)
- [IMeasurementStatusContext](interfaces/IMeasurementStatusContext.md)
- [IMessageDatabase](interfaces/IMessageDatabase.md)
- [IOnlineStatusContext](interfaces/IOnlineStatusContext.md)
- [ISignalData](interfaces/ISignalData.md)
- [ISignalDataEnvelope](interfaces/ISignalDataEnvelope.md)
- [IUndoObject](interfaces/IUndoObject.md)
- [IUndoState](interfaces/IUndoState.md)

## Type Aliases

- [MeasurementTraceDataOptions](type-aliases/MeasurementTraceDataOptions.md)
- [OnGoingOfflineCallback](type-aliases/OnGoingOfflineCallback.md)
- [OnGoingOnlineCallback](type-aliases/OnGoingOnlineCallback.md)

## Functions

- [useAvailableProtocols](functions/useAvailableProtocols.md)
- [useCombinedMeasurementTraceData](functions/useCombinedMeasurementTraceData.md)
- [useDevices](functions/useDevices.md)
- [useDevicesState](functions/useDevicesState.md)
- [useFixedPositionModeMeasurementData](functions/useFixedPositionModeMeasurementData.md)
- [useIsOnline](functions/useIsOnline.md)
- [useLanguage](functions/useLanguage.md)
- [useLocalizedStrings](functions/useLocalizedStrings.md)
- [useLogMessages](functions/useLogMessages.md)
- [useMaxDataBytes](functions/useMaxDataBytes.md)
- [useMeasurementSetup](functions/useMeasurementSetup.md)
- [useMeasurementSetupState](functions/useMeasurementSetupState.md)
- [useMeasurementStatus](functions/useMeasurementStatus.md)
- [useMeasurementStatusState](functions/useMeasurementStatusState.md)
- [useMessageData](functions/useMessageData.md)
- [useMessageDatabases](functions/useMessageDatabases.md)
- [useMessageLogFileFormats](functions/useMessageLogFileFormats.md)
- [~~useNewMeasurementData~~](functions/useNewMeasurementData.md)
- [useNodeStatus](functions/useNodeStatus.md)
- [useNumericRadix](functions/useNumericRadix.md)
- [useOnlineStatus](functions/useOnlineStatus.md)
- [useOnlineStatusSync](functions/useOnlineStatusSync.md)
- [useOverallStatusLevel](functions/useOverallStatusLevel.md)
- [useProjectData](functions/useProjectData.md)
- [useProjectDataSlice](functions/useProjectDataSlice.md)
- [useRecentProjectFiles](functions/useRecentProjectFiles.md)
- [useRunningPeriodicTransmissions](functions/useRunningPeriodicTransmissions.md)
- [useScrollModeMeasurementData](functions/useScrollModeMeasurementData.md)
- [useSessionData](functions/useSessionData.md)
- [useSessionDataSlice](functions/useSessionDataSlice.md)
- [useSignalData](functions/useSignalData.md)
- [useSignalDataEnvelopes](functions/useSignalDataEnvelopes.md)
- [useSignalLogFileFormats](functions/useSignalLogFileFormats.md)
- [useUndo](functions/useUndo.md)
- [useUndoRef](functions/useUndoRef.md)
- [useUndoSessionDataSlice](functions/useUndoSessionDataSlice.md)
- [useUserSettings](functions/useUserSettings.md)
- [useWorkspacePaneWithId](functions/useWorkspacePaneWithId.md)
