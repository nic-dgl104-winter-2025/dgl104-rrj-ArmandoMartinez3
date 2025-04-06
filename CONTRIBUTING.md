# H2OAI/WAVE

## Intended Contribution: Add Support for Null Option in `ui.dropdown` Component

### Links to the Project and Community

**GitHub repository:** https://github.com/h2oai/wave

**Code of Conduct:** `CODE_OF_CONDUCT.md`

**Contribution Guidelines:** `CONTRIBUTING.md`

**Related Issue:** #2449 – Feature Request: Support null option in `ui.dropdown`

-------

## Summary of the Issue

Currently, with the `ui.dropdown` component from H2O Wave does not support a `None` or null/default unselected option.
This limits the prompting of users to make choices. Instead, it defaults to the first option in the list.

This contribution shall implement support for but a `None` option in what the dropdown by way of allowing one special `DropdownChoice` with a `None` value.
Likely shown as something such as "Please select...". This would be especially helpful for form validation or logic flows where a choice must be consciously selected.

## Supporting Documentation

The issue itself provides a rationale and an expected behavior. Supporting a null/blank option is common in form UIs and is part of standard UX expectations. 
Adding this feature would improve the usability and flexibility of the dropdown component.

## Plan and Steps to Implement

1. Understand the Current Implementation
    - Review the source code for the `ui.dropdown` component in the Wave Python and frontend code.
    - Understand how `Dropdown.choice` and `Dropdown.value` are parsed and rendered.

2. Design a Backward-Compatible Approach
    - Ensure existing dropdowns that don’t include a null option will continue to behave normally.
    - Define how the `None` value is represented and serialized (e.g., an empty string or explicit `None`).

3. Modify Backend Python Interface
    - Allow a `DropdownChoice` with `value=None` or `value=""` to be included.
    - Update type annotations and validation logic if necessary.

4. Update Frontend (TypeScript)
    - Ensure that when rendering a dropdown, a null option can be displayed at the top.
    - Make sure it displays correctly and is selectable.
  
5. Test Behavior
    - Add a new example app to demonstrate this functionality in `/examples`.
    - Include tests for dropdowns that:
      - Have a null option
      - Don’t have one (default behavior unchanged)
      - Start with the null option selected

6. Update Documentation
    - Add notes about the null option to the dropdown component in `ui.py`.
    - Update README or relevant docs if needed.

7. Create a Pull Request
    - Reference issue **#2449.**
    - Provide a summary of what was added, example screenshots or code snippets, and any known edge cases or caveats.

## Code Review

**1. Backend – Update `ui.dropdown` to Accept a Null Option**

`ui.py`
``` python
# Before (simplified example)
@dataclass
class DropdownChoice:
    name: str
    label: Optional[str] = None
    disabled: Optional[bool] = None

# No changes needed here, but allow value=None in the dropdown value

@dataclass
class Dropdown:
    name: str
    choices: List[DropdownChoice]
    value: Optional[str] = None  # This already allows None!
```
- Allow one of the DropdownChoices to have name="" or name=None and display it as "Please select...".
- Add a helper or example to clarify what can be done.

**2. Frontend – Handle Empty Option**

`ui.tsx`
``` tsx
  {choices.map(c =>
    <option
      key={c.name ?? ''}
      value={c.name ?? ''}
      disabled={c.disabled}
    >
      {c.label ?? c.name}
    </option>
  )}
</Select>
```
- Make sure that if `value === null` or `value === ''`, that empty element is shown as selected.

**3. Add Example App**

In `examples/`, create a file like `dropdown_null_option.py`

``` python
from h2o_wave import main, app, Q, ui

@app('/')
async def serve(q: Q):
    if not q.client.initialized:
        q.page['form'] = ui.form_card(box='1 1 4 3', items=[
            ui.dropdown(
                name='dropdown',
                label='Choose an option',
                choices=[
                    ui.choice(name='', label='Please select...'),
                    ui.choice(name='a', label='Option A'),
                    ui.choice(name='b', label='Option B'),
                ],
                value=''  # Starts with null/empty value
            ),
            ui.button(name='submit', label='Submit', primary=True)
        ])
        q.client.initialized = True
    else:
        q.page['result'] = ui.markdown_card(
            box='1 4 4 1',
            title='You selected:',
            content=q.args.dropdown or 'Nothing selected.'
        )
    await q.page.save()
```

**4. Test Cases (Manual or Unit)**

- Verify that the dropdown displays "Please select..."

- Verify that when submitting without selecting, q.args.dropdown == '' or None

- Verify that other dropdowns without this value behave the same as before

## Conclusions

The implementation for a null or empty option in the ui.dropdown component addresses an important usability gap in the H2O Wave framework. Dropdowns used to select the list's initial choice; thus, users might submit default values, lacking an actual choice. This new feature allows developers to provide some placeholder-like option, such as “Please select…”, prompting users for consciously engaging into the dropdown before submission of a form.

This one small addition has such impact on user experience. This also has great impact upon form design. Through enabling of a default unselected state, developers gain control over form validation and application logic. It often becomes easier enough to detect if ever the user has made some deliberate choice, and that in turn allows always for clearer handling of input data.

Furthermore, such change has been placed in such a way to keep compatibility. Developers who do not wish at all to use this behavior can continue using dropdowns as they always have—nothing breaks or changes unless the new null option is explicitly added. This almost ensures a smooth adoption path without disrupting existing applications.

This contribution goes beyond the technical benefits. It also improves the developer experience. The further addition of a working example in the /examples folder serves as just a direct reference for precisely how to implement this behavior, lowering of the barrier for others to then use it well. Updated inline documentation further clarifies usage patterns, helping new as well as experienced users understand the intended functionality.

Eventually, this shift gets H2O Wave nearer to known UI/UX standards seen within similar web-based design platforms. Dropdowns' null/default states' support is standard, plus Wave gains flexibility; accessibility grows when one builds web apps.
