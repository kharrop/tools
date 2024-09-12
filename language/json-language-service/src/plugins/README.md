# JSON Language Service Plugins

Documentation is WIP - contributions welcomed!

## Tests

Each plugin has an associated test that runs through mock content. To run these tests, you can use the following command from root:

`bazel test //language/json-language-service:json-language-service_vitest --test_output=all`

## Plugins

### Complexity check

This plugin runs through content and calculates a complexity score to help teams understand how their content contributes to the potential performance impact in product.

Teams can set a `maxWarningLevel` that triggers a warning, as well as a `maxAcceptableComplexity` which will trigger an error.

A scoring breakdown of what this plugin looks for:

| Criteria                      | Points |
|-------------------------------|--------|
| Exp  in ACTION states (array) | 1      |
| View node                     | 1      |
| Asset node                    | 1      |
| Evaluation (@[]@)             | 2      |
| Expression ({{ }})            | 2      |

ASK KETAN:

- data set? - not seeing it being used, am I doing this right?
- evaulate only seems to run when there are monkey ears?
- is the nested binding calculations correct (add 2?)
- is there an example of a template I can look at to add as a test?
- views[] vs state_type (get errors when passing in another view?)