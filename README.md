https://www.nuget.org/packages/RadzenFork.Blazor/

This is a fork of the radzen-blazor library with new features that are not in the main library and without which it is impossible to do some things.

## Features:

### 1. Dynamically change the order in RadzenSplitter (without having to redraw everything)

Set **[UseGetIndex]** on *RadzenSplitter* and **[GetIndex]** on *RadzenSplitterPane* to correctly calculate the index when changing the order of panels to avoid placing the splitter at the end.

Example:
```
    <RadzenSplitter UseGetIndex="true">

        @if (FirstItems is { Count: > 0 })
        {
            @foreach (var c in FirstItems)
            {
                <RadzenSplitterPane GetIndex="() => Array.IndexOf(FirstItems.ToArray(), c)">
                    <SomeComponent1>
                    </SomeComponent1>
                </RadzenSplitterPane>
            }
        }

        @if (LastItem is not null)
        {
            <RadzenSplitterPane GetIndex="() => FirstItems.Count">
                <SomeComponent2>
                </SomeComponent2>
            </RadzenSplitterPane>
        }

    </RadzenSplitter>
```
