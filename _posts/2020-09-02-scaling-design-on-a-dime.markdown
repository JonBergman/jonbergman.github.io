---
layout: post
title:  "Scaling Design on a Dime"
date:   2020-09-02 08:51:11 -0400
---

In today's fast-paced startup environment, scaling design effectively can feel like a daunting challenge. However, by building a solid design system and leveraging off-the-shelf component libraries like Material UI or Chakra UI, startups can achieve the same level of design sophistication as large enterprises. In this post, we'll walk through the steps for scaling design efficiently through a component-based approach, focusing on design tokens and theming.

## Step 1: Define Your Design Primitives
The foundation of any design system starts with **design primitives**. These are the core elements that establish the visual identity and consistency of your product. Defining these primitives early on will make scaling design smoother as your product evolves.

### Key Primitives to Define:
- **Font Family & Typography Scale:** Establish your font choices and their hierarchy.
- **Spacing:** Define a consistent spacing scale (e.g., 4px, 8px, 16px, etc.).
- **Border Radius:** Set standardized border radius values for corners.
- **Colors:** Create a palette for primary, secondary, and neutral tones, including states like hover and active.
  
Once you've established these primitives, abstract them into **design tokens**.

### Example Tokens:
```scss
--font-family-base: "Inter, sans-serif";
--font-size-base: 16px;
--spacing-base: 8px;
--border-radius-base: 4px;
--color-primary: #0055ff;
--color-secondary: #ff5733;
```

These tokens serve as the building blocks that can be reused consistently across your product, both in design files and code.

## Step 2: Create Semantic Design Tokens
To ensure your design scales well, use the base primitives to create **semantic tokens**—these tokens map to specific use cases rather than raw values. For example, instead of using `--color-primary` directly, create a more meaningful name like `--button-background`.

### Semantic Tokens Example:
```scss
--button-background: var(--color-primary);
--input-border-radius: var(--border-radius-base);
```

By using semantic tokens, you're able to maintain flexibility. As the design evolves, you can modify the primitive values without needing to adjust the entire system.

## Step 3: Design Components in Figma
Once your tokens are in place, it's time to start designing your components in **Figma**. Design these components with the primitives and semantic tokens in mind, but don’t feel constrained by having to map everything 1:1 with an existing component library.

For example, Material UI might have a Button component, but your product may need a custom button variant. You can use Figma to design components that follow your tokens and ensure consistency across the design team.

> **Pro Tip**: Consider creating master components in Figma that designers can use across multiple files, ensuring consistency in design and reducing duplication.

## Step 4: Theme an Off-the-Shelf Component Library
The next step is to apply your design system to the codebase. Component libraries like **Material UI** or **Chakra UI** provide extensive theming capabilities that allow you to map your design tokens directly to UI components. By overriding the default theme, you can quickly adapt these components to fit your brand.

### Example Theming (Material UI):
```javascript
const theme = createTheme({
  palette: {
    primary: {
      main: '#0055ff',
    },
    secondary: {
      main: '#ff5733',
    },
  },
  typography: {
    fontFamily: '"Inter", sans-serif',
  },
  shape: {
    borderRadius: 4,
  },
});
```

This approach gets you most of the way there by leveraging pre-built components with your custom theming.

## Step 5: Utilize the Overrides API for Additional Customization
While theming will cover a lot of the base styles, you'll often want to adjust components further to match your Figma designs precisely. Libraries like Material UI offer an **Overrides API** to modify default props and styles.

### Example Overrides (Material UI):
```javascript
const theme = createTheme({
  components: {
    MuiButton: {
      defaultProps: {
        disableElevation: true,
      },
      styleOverrides: {
        root: {
          textTransform: 'none', // Remove uppercase styling from buttons
          borderRadius: 'var(--border-radius-base)',
        },
      },
    },
  },
});
```

These overrides allow for a high degree of customization, ensuring that your UI aligns with the Figma components, even if they're not a 1:1 match with the library's base components.

## Step 6: Build Unique Components When Needed
Startups often have unique business needs that can't always be met by off-the-shelf libraries. When this is the case, you can build custom components from scratch. The good news is that with your design system and tokens in place, even custom-built components can maintain consistency.

Use the design tokens for typography, colors, spacing, and other primitives to build out these unique components, ensuring they blend seamlessly with the rest of your UI.

### Example Custom Component:
```javascript
const CustomCard = styled('div')({
  backgroundColor: 'var(--color-primary)',
  padding: 'var(--spacing-base) var(--spacing-large)',
  borderRadius: 'var(--border-radius-base)',
});
```

## Conclusion
Scaling design as a startup doesn’t require a large team or enterprise-level resources. By defining design primitives, creating semantic tokens, and theming off-the-shelf libraries, startups can build a flexible, scalable design system that grows alongside their product. Whether you're using popular libraries or building custom components, your design system will serve as the foundation for delivering a consistent, high-quality user experience.

Now it's time to get designing!