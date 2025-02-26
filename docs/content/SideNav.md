---
title: SideNav
---

The Side Nav is a vertical list of navigational links, typically used on the left side of a page. For maximum flexibility, **SideNav elements have no default width or positioning.**

## Default example

```jsx live
<SideNav bordered maxWidth={360} aria-label="Main">
  <SideNav.Link href="#account">
    <Text>Account</Text>
  </SideNav.Link>
  <SideNav.Link href="#home" selected>
    <Text>Profile</Text>
  </SideNav.Link>
  <SideNav.Link href="#emails">
    <Text>Emails</Text>
  </SideNav.Link>
  <SideNav.Link href="#notifications">
    <Text>Notifications</Text>
  </SideNav.Link>
</SideNav>
```

Different kinds of content can be added inside a SideNav item. Use system props to further style them if needed.

## Full variant

Add the `variant='full'` prop to a `SideNav.Link` to spread child elements across the link, which is useful for status icons, labels, and the like.

```jsx live
<SideNav bordered maxWidth={360} aria-label="Main">
  <SideNav.Link href="#url">
    <Text>Text Only</Text>
  </SideNav.Link>
  <SideNav.Link href="#url">
    <Avatar size={16} mr={2} src="https://avatars.githubusercontent.com/hubot?s=32" />
    <Text>With an avatar</Text>
  </SideNav.Link>
  <SideNav.Link href="#url">
    <StyledOcticon sx={{mr: 2}} size={16} icon={ZapIcon} />
    <Text>With an Octicon</Text>
  </SideNav.Link>
  <SideNav.Link href="#url" variant="full" selected>
    <Text>With a status icon</Text>
    <StyledOcticon sx={{mr: 2}} size={16} icon={DotIcon} color="icon.success" />
  </SideNav.Link>
  <SideNav.Link href="#url" variant="full">
    <Text>With a label</Text>
    <Label outline>label</Label>
  </SideNav.Link>
  <SideNav.Link href="#url" variant="full">
    <Text>With a counter</Text>
    <CounterLabel>16</CounterLabel>
  </SideNav.Link>
  <SideNav.Link href="#url">
    <Heading as="h5" sx={{fontSize: 1}}>
      A heading
    </Heading>
    <Text>and some more content</Text>
  </SideNav.Link>
</SideNav>
```

## Lightweight variant

Add the `variant="lightweight"` prop to `SideNav` to render an alternative, more lightweight version that has items with no borders and are more condensed.

```jsx live
<Box
  borderWidth="1px"
  borderStyle="solid"
  borderColor="border.primary"
  borderRadius={2}
  p={3}
  backgroundColor="bg.secondary"
  maxWidth={360}
>
  <Box
    borderStyle="solid"
    borderColor="border.primary"
    borderWidth={0}
    borderBottomWidth={1}
    borderRadius={0}
    mb={2}
    pb={1}
  >
    <Heading as="h5" fontSize={1} color="text.secondary">
      Menu
    </Heading>
  </Box>
  <SideNav variant="lightweight">
    <SideNav.Link href="#url">
      <Text>Account</Text>
    </SideNav.Link>
    <SideNav.Link href="#url" selected>
      <Text>Profile</Text>
    </SideNav.Link>
    <SideNav.Link href="#url">
      <Text>Emails</Text>
    </SideNav.Link>
    <SideNav.Link href="#url">
      <Text>Notifications</Text>
    </SideNav.Link>
  </SideNav>
</Box>
```

It can also appear nested, as a sub navigation. Use margin/padding [System Props](/system-props) to add indentation.

```jsx live
<SideNav bordered maxWidth={360}>
  <SideNav.Link href="#url">
    <StyledOcticon mr={2} size={16} icon={PersonIcon} />
    <Text>Account</Text>
  </SideNav.Link>
  <SideNav.Link href="#url" selected>
    <StyledOcticon mr={2} size={16} icon={OctofaceIcon} />
    <Text>Profile</Text>
  </SideNav.Link>

  <SideNav bordered variant="lightweight" py={3} pl={6} backgroundColor="sidenav.selectedBg">
    <SideNav.Link href="#url" selected>
      <Text>Sub item 1</Text>
    </SideNav.Link>
    <SideNav.Link href="#url">
      <Text>Sub item 2</Text>
    </SideNav.Link>
    <SideNav.Link href="#url">
      <Text>Sub item 3</Text>
    </SideNav.Link>
  </SideNav>

  <SideNav.Link href="#url">
    <StyledOcticon mr={2} size={16} icon={MailIcon} />
    <Text>Emails</Text>
  </SideNav.Link>
</SideNav>
```

## Usage with React Router

If using React Router, you can use the `as` prop to render the element as a `NavLink`. React Router will automatically handle setting `aria-current="page"` for you.

```
<SideNav.Link as={NavLink} to="...">...</SideNav.Link>
```

## System props

<Note variant="warning">

System props are deprecated in all components except [Box](/Box). Please use the [`sx` prop](/overriding-styles) instead.

</Note>

`SideNav` components get `COMMON`, `BORDER`, `LAYOUT`, and `FLEX` system props. `SideNav.Link` components get `COMMON` and `TYPOGRAPHY` system props. Read our [System Props](/system-props) doc page for a full list of available props.

## Component props

### SideNav

| Name     | Type    | Default  | Description                                                                    |
| :------- | :------ | :------: | :----------------------------------------------------------------------------- |
| as       | String  |  'nav'   | Sets the HTML tag for the component.                                           |
| bordered | Boolean |  false   | Renders the component with a border.                                           |
| variant  | String  | 'normal' | Set to `lightweight` to render [in a lightweight style](#lightweight-variant). |

### SideNav.Link

| Name      | Type    | Default  | Description                                                                                       |
| :-------- | :------ | :------: | :------------------------------------------------------------------------------------------------ |
| as        | String  |   'a'    | Sets the HTML tag for the component.                                                              |
| href      | String  |          | URL to be used for the Link                                                                       |
| muted     | Boolean |  false   | Uses a less prominent shade for Link color, and the default link shade on hover                   |
| selected  | Boolean |  false   | Sets the link as selected, giving it a different style and setting the `aria-current` attribute.  |
| underline | Boolean |  false   | Adds underline to the Link                                                                        |
| variant   | String  | 'normal' | Set to `full` to render [a full variant](#full-variant), suitable for including icons and labels. |
