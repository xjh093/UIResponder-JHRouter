# UIResponder-JHRouter
Say goodbye to 「block and delegate」

```
 - (void)jh_routerWithSelector:(NSString *)selector sender:(id)sender info:(NSDictionary *)info{
    if ([self respondsToSelector:NSSelectorFromString(selector)]){
        [self performSelector:NSSelectorFromString(selector) withObjects:info];
    }
    else if ([selector isEqualToString:@"xxx"]) {
        // do something with info.
    }
    else{
 
        // This is important!!!
        // if you can't handle it, pass it to nextResponder to handle it.
 
        [self.nextResponder jh_routerWithSelector:selector sender:sender info:info];
    }
 }
```
