---
layout: post
title: "Refactoring UI with examples"
---

I recently read [Refactoring UI](https://www.refactoringui.com/), which was excellent. It’s chock-full of practical advice, and you can feel that a lot of hard-learned lessons were condensed into the book.

Here are a few small takeaways with examples of how I applied them at work.

### Balance weight and contrast for icons

What makes bold text stand out? The answer is that even though it's the same color as regular text, it's got more "Pixels per cm" than regular text.

This is important when we think of icons. Icons can accidentally feel bold because like strong text, filled icons have more "Pixels per cm" than text. This can draw attention away from text, and onto icons, which is probably not your intention.

Take a look at these two screenshots:

|--|--|
|![](https://paper-attachments.dropboxusercontent.com/s_F908D7B96894A47C2C02C069D83E2EBE5618DE064F12A53F3433C6DE7709968D_1716979128215_image.png)  | ![](https://paper-attachments.dropboxusercontent.com/s_F908D7B96894A47C2C02C069D83E2EBE5618DE064F12A53F3433C6DE7709968D_1716983236904_image.png) |

<br>
In the second I’ve reduced the contrast of the only “filled” icon on the page, next to the text "onboarding checklist". Before, it stuck out like a sore thumb even though it was the same color as the others due to its high color density.

It’s not a huge difference, but the principle is powerful. I’ll be looking out for “overpowering” icons now that I know how to pull attention away from them by tweaking their contrast.

### Communicate hierarchy, not just semantics for actions

What's wrong with this component?

![](https://paper-attachments.dropboxusercontent.com/s_F908D7B96894A47C2C02C069D83E2EBE5618DE064F12A53F3433C6DE7709968D_1715765092548_image.png)

On one hand the color helps make the semantics clear for the buttons. Red reinforces the destructive action, green the happy path, and blue the additional option. On the other, the design completely fails to capture their heirarchy.

> Every action on a page sits somewhere in a pyramid of importance. Most pages only have one true primary action, a couple of less important secondary actions, and a few seldom used tertiary actions.
>
> **Primary actions should be obvious.** Solid, high contrast background colors work great here. Semantics are secondary.
>
> **Secondary actions should be clear but not prominent.** Outline styles or lower contrast background colors are great options.
>
> **Tertiary actions should be discoverable but unobtrusive.** Styling these actions like links is usually the best approach.

This is an approach we’ve taken in AirManual, as you can see here.

![](https://paper-attachments.dropboxusercontent.com/s_F908D7B96894A47C2C02C069D83E2EBE5618DE064F12A53F3433C6DE7709968D_1718571284544_Zrzut+ekranu+2024-06-16+o+21.54.15.png)

Rather than using color to confer semantics, we've focused on conveying hierarchy. I think the result looks great.

### Use as much of the screen as you need, no more

You don’t need to use the whole screen - if you only need 600px to show something, just use 600px.

This is something we've been successful with in some designs, but not globally across our application. Take the workspace navigator view for example.

![User-uploaded image: image.png](https://paper.dropbox.com/ep/redirect/image?url=https%3A%2F%2Fpaper-attachments.dropboxusercontent.com%2Fs_F908D7B96894A47C2C02C069D83E2EBE5618DE064F12A53F3433C6DE7709968D_1718632995397_image.png&hmac=QQcISFk9H6wR3wRKYBqsrtr4BqUViyE7Ju45IlC4UgU%3D&width=1490)

Look at that, nailed it. Noticing and then applying this rule consistently, take a look at the effect on the team members page. Much less dragging your eyes from left to right is needed to review members and their permissions.

|--|--|
| ![](https://paper.dropbox.com/ep/redirect/image?url=https%3A%2F%2Fpaper-attachments.dropboxusercontent.com%2Fs_F908D7B96894A47C2C02C069D83E2EBE5618DE064F12A53F3433C6DE7709968D_1716983332674_image.png&hmac=Abtw6NlJPg4mS4OJEIfxaJaRdmawNBW5EdH5UNkcUgk%3D) | ![](https://paper.dropbox.com/ep/redirect/image?url=https%3A%2F%2Fpaper-attachments.dropboxusercontent.com%2Fs_F908D7B96894A47C2C02C069D83E2EBE5618DE064F12A53F3433C6DE7709968D_1716983454542_image.png&hmac=6X3m4PD0lHDLnsax9IHJQIZrQkNmjZ8h%2BGCMqPUt%2FDA%3D) |

<br>

### In summary


If you're a software engineer who designs user-facing features, it's worth learning about design. Refactoring UI is filled with advice, some of it nonobvious, about how to improve every aspect of your web app design. I have read more than a few books on UX and UI design, and I still came away with a good selection of tools to use in the future.

If you get the chance, pick it up!