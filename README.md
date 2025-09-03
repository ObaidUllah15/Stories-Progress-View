StoriesProgressView
====

Library that shows a horizontal progress like Instagram, WhatsApp and Facebook stories.
/1.0
[![](https://jitpack.io/ObaidUllah15/Stories-Progress-View.svg)](https://jitpack.io/#ObaidUllah15/Stories-Progress-View)

<img src="image/capture.png" width=200 />

<img src="image/image.gif" width=200 /> 

How to Use
----

To see how a StoriesProgressView can be added to your xml layouts, check the sample project.

```xml
    <jp.shts.android.storiesprogressview.StoriesProgressView
        android:id="@+id/stories"
        android:layout_width="match_parent"
        android:layout_height="3dp"
        android:layout_gravity="top"
        android:layout_marginTop="8dp" />
```
Overview

```java
public class YourActivity extends AppCompatActivity implements StoriesProgressView.StoriesListener {
    private StoriesProgressView storiesProgressView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        storiesProgressView = (StoriesProgressView) findViewById(R.id.stories);
        storiesProgressView.setStoriesCount(PROGRESS_COUNT); // <- set stories
        storiesProgressView.setStoryDuration(1200L); // <- set a story duration
        storiesProgressView.setStoriesListener(this); // <- set listener
        storiesProgressView.startStories(); // <- start progress
    }

    @Override
    public void onNext() {
        Toast.makeText(this, "onNext", Toast.LENGTH_SHORT).show();
    }

    @Override
    public void onPrev() {
        // Call when finished revserse animation.
        Toast.makeText(this, "onPrev", Toast.LENGTH_SHORT).show();
    }

    @Override
    public void onComplete() {
        Toast.makeText(this, "onComplete", Toast.LENGTH_SHORT).show();
    }

    @Override
    protected void onDestroy() {
        // Very important !
        storiesProgressView.destroy();
        super.onDestroy();
    }
}
```

Skip and Reverse story
---

<img src="image/skip-reverse.gif" width=200 />

```java
  storiesProgressView.skip();
  storiesProgressView.reverse();
```

Pause and Resume story
---
<img src="image/pause-resume.gif" width=200 />

```java
  storiesProgressView.pause();
  storiesProgressView.resume();
```


Install
---

Add it in your root build.gradle at the end of repositories:

```groovy
allprojects {
    repositories {
        ...
        maven { url "https://jitpack.io" }
    }
}

```

Add the dependency

```
dependencies {
    implementation("com.github.ObaidUllah15:Stories-Progress-View:1.0")
}

```
