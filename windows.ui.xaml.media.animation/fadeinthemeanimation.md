---
-api-id: T:Windows.UI.Xaml.Media.Animation.FadeInThemeAnimation
-api-type: winrt class
---

<!-- Class syntax.
public class FadeInThemeAnimation : Windows.UI.Xaml.Media.Animation.Timeline, Windows.UI.Xaml.Media.Animation.IFadeInThemeAnimation
-->

# Windows.UI.Xaml.Media.Animation.FadeInThemeAnimation

## -description
Represents the preconfigured opacity animation that applies to controls when they are first shown.

## -xaml-syntax
```xaml
<FadeInThemeAnimation ... />
```


## -remarks

## -examples
The following example applies a [FadeInThemeAnimation](fadeinthemeanimation.md) and [FadeOutThemeAnimation](fadeoutthemeanimation.md) to a rectangle.


<!--  
      <p xml:space="preserve">
            <TRANSLATE_MANUALLY>
              <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">
                <linkText>Run this sample</linkText>
                <linkUri>http://go.microsoft.com/fwlink/p/?linkid=139798&amp;sref=BackEase_scale</linkUri>
              </externalLink>
            </TRANSLATE_MANUALLY>
          </p>-->



[!code-xml[FadeThemeAnimation](../windows.ui.xaml.media.animation/code/FadeInThemeAnimation/csharp/BlankPage.xaml#SnippetFadeThemeAnimation)]

[!code-cs[FadeThemeAnimation_code](../windows.ui.xaml.media.animation/code/FadeInThemeAnimation/csharp/BlankPage.xaml.cs#SnippetFadeThemeAnimation_code)]

## -see-also
[Timeline](timeline.md), [Animating fades](http://msdn.microsoft.com/library/21be4a46-8d63-451f-ae34-23c9e11f62da), [Guidelines and checklist for fade animations](XREF:TODO:m_personality.guidelines_for_fade_animations)
