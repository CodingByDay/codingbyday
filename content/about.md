+++
title = "About"
date = "2022-09-02"
aliases = ["about-us","about-hugo","contact"]
[ author ]
  name = "Janko Jovičić"
+++

I am a software engineer living in Slovenia. I have several years of experience in ASP.NET, SQL, Java, Python, and other programming languages. Most of my work is related to WMS systems and business automation in C#. 

This is my website which will contain day-to-day information about software engineering
with useful information about current projects and tips on development aimed to help people improve their understanding of programming as well as personal promotion and business inquiries.

I am currently employed by IN SIST d.o.o. as a .NET software engineer. 

**Regards,**
{{< highlight cs "linenos=table,hl_lines=8 15-17,linenostart=1" >}}
 private async void SavePositions(List<MorePallets> payload)
        {
            progress = new ProgressDialogClass();
            progress.ShowDialogSync(this, "Saving position.");
            foreach (var x in payload)
            {
                await SaveMoveItemBatch(x);
            }
            progress.StopDialogSync();
        }
{{< / highlight >}}


