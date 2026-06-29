[**Kvaser CanKing GUI Extensions SDK v7.5.0**](../README.md)

***

[Kvaser CanKing GUI Extensions SDK](../modules.md) / controls

# controls

This module includes UI controls implemented as React components.

To be able to use these controls the CanKingDataProvider component must be present in the
component tree above your component. Normally the CanKingDataProvider is added
at the root of the component tree.

## Example

```tsx
import { useSearchParams } from 'react-router-dom';
import { useProjectData } from '@kvaser/canking-api/canking';
import { CanChannelSelectControl, FillBox } from '@kvaser/canking-api/controls';

// If any data should be stored in the project file then add it to this interface
interface IProjectViewData {
  // This is an example showing how to store the selected channel id to the project file
  channelId: string;
}

// Define any default values for the project data that will be used when the component is created
const defaultProjectViewData: IProjectViewData = {
  channelId: '',
};

function WorkspaceView() {
  // Get this view's unique id from search params
  const [searchParams] = useSearchParams();
  const idString = searchParams.get('id');
  const id = idString !== null ? Number.parseInt(idString, 10) : -1;

  // Use the useProjectData hook to serialize/deserialize your view data to the project
  const [projectData, setProjectData] = useProjectData<IProjectViewData>(id, defaultProjectViewData);

  // A callback that will get the new selected channel id and save it to the project data
  const onChannelIdentifierChange = (channelId: string) => {
    const data = { ...projectData };
    data.channelId = channelId;
    setProjectData(data);
  };

  return (
    <FillBox component="form">
      <div>Add your elements here!</div>
      <div>This is an example how to use the CanChannelSelectControl:</div>
      <CanChannelSelectControl
        channelIdentifier={projectData.channelId}
        onChannelIdentifierChange={onChannelIdentifierChange}
        hideSectionControl
      />
    </FillBox>
  );
}

export default WorkspaceView;
```

## Interfaces

- [ButtonGroupProps](interfaces/ButtonGroupProps.md)
- [ButtonProps](interfaces/ButtonProps.md)
- [CanChannelSelectControlProps](interfaces/CanChannelSelectControlProps.md)
- [CanIdentifierControlProps](interfaces/CanIdentifierControlProps.md)
- [CanIdentifierFrameControlProps](interfaces/CanIdentifierFrameControlProps.md)
- [CanIdentifierGeneratorControlProps](interfaces/CanIdentifierGeneratorControlProps.md)
- [CanIdentifierGeneratorSettingsControlProps](interfaces/CanIdentifierGeneratorSettingsControlProps.md)
- [CheckboxControlProps](interfaces/CheckboxControlProps.md)
- [ColorControlProps](interfaces/ColorControlProps.md)
- [ContextMenuProps](interfaces/ContextMenuProps.md)
- [DividerItemProps](interfaces/DividerItemProps.md)
- [DropdownButtonChildrenProps](interfaces/DropdownButtonChildrenProps.md)
- [DropdownButtonProps](interfaces/DropdownButtonProps.md)
- [DropdownButtonTextItemsProps](interfaces/DropdownButtonTextItemsProps.md)
- [DropdownPanelProps](interfaces/DropdownPanelProps.md)
- [FormControlRowProps](interfaces/FormControlRowProps.md)
- [IExtensionWorkspaceViewProps](interfaces/IExtensionWorkspaceViewProps.md)
- [ILocalizedStrings](interfaces/ILocalizedStrings.md)
- [InlineEditorProps](interfaces/InlineEditorProps.md)
- [LabelProps](interfaces/LabelProps.md)
- [LinChannelSelectControlProps](interfaces/LinChannelSelectControlProps.md)
- [LinIdentifierControlProps](interfaces/LinIdentifierControlProps.md)
- [LinIdentifierFrameControlProps](interfaces/LinIdentifierFrameControlProps.md)
- [LinIdentifierGeneratorControlProps](interfaces/LinIdentifierGeneratorControlProps.md)
- [LinIdentifierGeneratorSettingsControlProps](interfaces/LinIdentifierGeneratorSettingsControlProps.md)
- [NumberRangeControlProps](interfaces/NumberRangeControlProps.md)
- [RadioControlProps](interfaces/RadioControlProps.md)
- [RadioGroupControlProps](interfaces/RadioGroupControlProps.md)
- [SectionControlProps](interfaces/SectionControlProps.md)
- [SelectControlProps](interfaces/SelectControlProps.md)
- [SelectedSignalInfo](interfaces/SelectedSignalInfo.md)
- [SelectedSignalInfoChangeArgs](interfaces/SelectedSignalInfoChangeArgs.md)
- [SelectMessageDialogProps](interfaces/SelectMessageDialogProps.md)
- [SelectSignalDialogProps](interfaces/SelectSignalDialogProps.md)
- [SelectSignalsControlProps](interfaces/SelectSignalsControlProps.md)
- [TableColumn](interfaces/TableColumn.md)
- [TableControlProps](interfaces/TableControlProps.md)
- [TextControlProps](interfaces/TextControlProps.md)
- [ToggleButtonGroupProps](interfaces/ToggleButtonGroupProps.md)
- [ToggleButtonProps](interfaces/ToggleButtonProps.md)
- [ToolbarControlProps](interfaces/ToolbarControlProps.md)
- [toolbarItem](interfaces/toolbarItem.md)
- [ValidateableTextControlProps](interfaces/ValidateableTextControlProps.md)

## Type Aliases

- [canIdentifierGeneratorType](type-aliases/canIdentifierGeneratorType.md)
- [canIdentifierType](type-aliases/canIdentifierType.md)
- [ContextMenuOption](type-aliases/ContextMenuOption.md)
- [extensionEventChannels](type-aliases/extensionEventChannels.md)
- [linIdentifierGeneratorType](type-aliases/linIdentifierGeneratorType.md)
- [SelectOption](type-aliases/SelectOption.md)
- [StringsMap](type-aliases/StringsMap.md)

## Variables

- [FillBox](variables/FillBox.md)
- [OneLineButton](variables/OneLineButton.md)
- [SizedBox](variables/SizedBox.md)
- [TabsPanel](variables/TabsPanel.md)

## Functions

- [CanChannelSelectControl](functions/CanChannelSelectControl.md)
- [CanIdentifierControl](functions/CanIdentifierControl.md)
- [CanIdentifierFrameControl](functions/CanIdentifierFrameControl.md)
- [CanIdentifierGeneratorControl](functions/CanIdentifierGeneratorControl.md)
- [CanIdentifierGeneratorSettingsControl](functions/CanIdentifierGeneratorSettingsControl.md)
- [CanKingDataProvider](functions/CanKingDataProvider.md)
- [CheckboxControl](functions/CheckboxControl.md)
- [ColorControl](functions/ColorControl.md)
- [ColumnItemControl](functions/ColumnItemControl.md)
- [ContextMenu](functions/ContextMenu.md)
- [DropdownButton](functions/DropdownButton.md)
- [DropdownButtonTextItems](functions/DropdownButtonTextItems.md)
- [DropdownPanel](functions/DropdownPanel.md)
- [FormControlRow](functions/FormControlRow.md)
- [InlineEditor](functions/InlineEditor.md)
- [LinChannelSelectControl](functions/LinChannelSelectControl.md)
- [LinIdentifierControl](functions/LinIdentifierControl.md)
- [LinIdentifierFrameControl](functions/LinIdentifierFrameControl.md)
- [LinIdentifierGeneratorControl](functions/LinIdentifierGeneratorControl.md)
- [LinIdentifierGeneratorSettingsControl](functions/LinIdentifierGeneratorSettingsControl.md)
- [NumberRangeControl](functions/NumberRangeControl.md)
- [RadioControl](functions/RadioControl.md)
- [RadioGroupControl](functions/RadioGroupControl.md)
- [SectionControl](functions/SectionControl.md)
- [SelectControl](functions/SelectControl.md)
- [SelectMessageDialog](functions/SelectMessageDialog.md)
- [SelectSignalsControl](functions/SelectSignalsControl.md)
- [TableControl](functions/TableControl.md)
- [TextControl](functions/TextControl.md)
- [ToolbarControl](functions/ToolbarControl.md)
- [useColumnItem](functions/useColumnItem.md)
- [useColumnItems](functions/useColumnItems.md)
- [ValidateableTextControl](functions/ValidateableTextControl.md)
