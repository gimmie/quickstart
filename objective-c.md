# Objective-C API

Objective-C API is a static library for calling Gimmie. The library can download
from [release tab](https://github.com/gimmie/objective-c/releases).

## Integrating Gimmie API

To add Gimmie to your project, Download release and add the whole library by
drag all files to your project. After that go to your project properties, select
your project target and under __Link Binary With Libralies__ click on __+__
sign and select __libGimmieAPI.a__ file.

## Sample API code

```Objective-C
@import Foundation

#import GMService.h

@interface SampleClass : NSObject

- (void) doSomethingWithGimmie;

@end

@implementation SampleClass

- (void) doSomethingWithGimmie
{
  GMService *service = [GMService sharedServiceWithKey: @"game_key_from_portal" secret: @"game_secret_from_portal"];
  [service login: @"your_user_id" withName:@"Name shows in claim page" andEmail: @"Email shows in claim page"];
  [service triggerEventName: @"sample_event"
                   callback: ^(NSError *error, GMCombineResponse *response) {
                     // Handle with response here
                   }];
}

@end

```
