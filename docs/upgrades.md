# Upgrades

Upgrades are stored in the following format:

``upgrades: {
  rows: # of rows
  cols: # of columns
  11: {
    desc: "Blah",
    etc
  }
  etc
}``

You can use hasUpg(layer, id) to determine if the player has an upgrade. This is useful for implementing bonuses.

Each upgrade should have an id where the first digit is the row and the second digit is the column.
Individual upgrades can have these features:

- desc: A description of the upgrade's effect. *You will also have to implement the effect where it is applied.*

- effect(): **optional**, A function that calculates and returns the current values of any bonuses from the upgrade.
    Can return a value or an object containing multiple values.

- effectDisp(effects): **optional**, A function that returns a display of the current effects of the upgrade with
                       formatting. Default behavior is to just display the a number appropriately formatted.

- cost: A Decimal for the cost of the upgrade. By default, upgrades cost the main prestige currency for the layer.

- unl(): A function returning a bool to determine if the upgrade is visible or not.

- onPurchase() - **optional**, this function will be called when the upgrade is purchased.
                 Good for upgrades like "makes this layer act like it was unlocked first".

By default, upgrades use the main prestige currency for the layer. You can include these to change them:
- currencyDisplayName: **optional**, the name to display for the currency for the upgrade
- currencyInternalName: **optional**, the internal name for that currency
- currencyLayer: **optional**, the internal name of the layer that currency is stored in.
                 If it's not in a layer (like Points), omit.

