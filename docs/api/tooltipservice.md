# TooltipService

# Example

```typescript

import * as tooltip from 'powerbi-visuals-utils-tooltiputils';

import * as $ from "jquery";
import * as d3 from "d3";

export class YourVisual implements IVisual {
    // implementation of IVisual.
    private tooltipServiceWrapper: tooltip.ITooltipServiceWrapper;
    constructor(options: VisualConstructorOptions) {
        tooltip.createTooltipServiceWrapper(options.host.tooltipService,options.element);
        this.tooltipServiceWrapper = tooltip.createTooltipServiceWrapper(options.host.tooltipService, $("body").get(0));
    }
    
    public update(options: VisualUpdateOptions) {
         var element = d3.select("#myContainer .td").data([{
           tooltipInfo: [{
               displayName: "Test",
               value: "Değer"
           }
            ]
        }]);

        this.tooltipServiceWrapper.addTooltip<tooltip.TooltipEnabledDataPoint>(element, (eventArgs: tooltip.TooltipEventArgs<tooltip.TooltipEnabledDataPoint>) => {
            return eventArgs.data.tooltipInfo;
        });
   }
}
```

