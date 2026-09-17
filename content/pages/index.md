---
type: PageLayout
title: Home
colors: colors-a
backgroundImage:
  type: BackgroundImage
  url: /images/IMG_0625.jpeg
  backgroundSize: cover
  backgroundPosition: center
  backgroundRepeat: no-repeat
  opacity: 75
sections:
  - elementId: ''
    colors: colors-f
    backgroundSize: full
    title: 'Hi, I am massimo'
    subtitle: >-
      I spend a lot of time thinking about how cities get built, and who they
      get built for. Some days that means housing supply and land use. Other
      times it's the financing behind a project, or the zoning rules quietly
      deciding what's possible long before anyone breaks ground. What interests
      me most is the gap between how development is supposed to work and how it
      actually does. Access and opportunity matter to me, but I'm just as
      focused on the people who get priced out when a neighborhood improves. I
      got here sideways: astrophysics research at the University of Miami,
      economics at Vanderbilt, then writing the requirements for two internal AI
      systems at TD Bank. Different problems, same habit of pulling at a dataset
      until it gives something up. Now I'm finishing a master's in economics at
      Columbia. This site is where I work through it. Sometimes that means
      digging into the numbers. Other times it means calling out what doesn't
      add up, or just pushing back when the story feels too neat. I don't
      pretend to have everything figured out. But I do believe that asking the
      right questions matters, especially in a world that rarely slows down for
      answers.
    styles:
      self:
        height: auto
        width: wide
        margin:
          - mt-0
          - mb-0
          - ml-0
          - mr-0
        padding:
          - pt-36
          - pb-48
          - pl-4
          - pr-4
        alignItems: center
        justifyContent: center
        flexDirection: row-reverse
      title:
        textAlign: left
      subtitle:
        textAlign: left
      text:
        textAlign: left
      actions:
        justifyContent: flex-start
    type: HeroSection
    actions: []
    text: |
      Check out my info page to learn more about me.
  - type: FeaturedPostsSection
    elementId: ''
    colors: colors-f
    variant: variant-d
    subtitle: Featured Posts
    showFeaturedImage: false
    actions:
      - type: Link
        label: See all posts
        url: /blog
    posts:
      - content/pages/blog/Economic_Recession_Model.md
      - content/pages/blog/BTC_VS_SPY_VS_QQQ.md
      - content/pages/blog/PostUnderGradPost.md
    showDate: true
    showExcerpt: true
    showReadMoreLink: true
    styles:
      self:
        height: auto
        width: narrow
        margin:
          - mt-0
          - mb-0
          - ml-0
          - mr-0
        padding:
          - pt-28
          - pb-48
          - pl-4
          - pr-4
        justifyContent: center
        borderRadius: none
        borderWidth: 0
        borderStyle: none
        borderColor: border-dark
      title:
        textAlign: left
      subtitle:
        textAlign: left
      actions:
        justifyContent: flex-end
---
