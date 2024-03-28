new少点







'?.' on a type deriving from 'UnityEngine.Object' bypasses the lifetime check on the underlying Unity engine object

？用在了派生自ueObj的物体上，绕过了unity obj的生命周期

如果使用空合并或条件运算符，则表意不明确，并且可能绕过预期的生命周期检查。如果打算进行生命周期检查，推荐使用与 null 或布尔比较的显式比较。若不打算进行生命周期检查，请调用 System.Object.ReferenceEquals() 以明确表意。