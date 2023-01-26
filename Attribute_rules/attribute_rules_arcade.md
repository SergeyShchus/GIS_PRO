

Якщо в полі Hammer Test порожнє значення, або якщо в полі Pole Condition порожнє значення, або якщо в полі Wiring Condition порожнє значення, або якщо в полі Panel Condition порожнє значення, повернути значення false. Інакше повернути true.

```
// Check if the values in the Hammer Test, Pole Condition, Wiring Condition, or Panel Condition fields are null (empty).
if  (IsEmpty($feature.HammerTest) ||
isEmpty($feature.PoleCond) ||
isEmpty($feature.WiringCond) ||
isEmpty($feature.PanelCond))

// If any of the fields above are null, return false.
return false

// Otherwise, return true.
return true
```



```
// Return the mean of four test values
Mean($feature.HammerTest,$feature.WiringCond,$feature.PanelCond,$feature.PoleCond)

```
