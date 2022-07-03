> link https://github.com/lindlof/secret_rock_paper_scissors/blob/master/contract/src/contract.rs


> init is winning margin in % and payout wallet.
> buyin is dependent on total to win.
> entropy padding.

> 1 buyin.
> demo got 9 win and 10 losses 
> 5% profit
> entropy: entropy+height+sententropy

    let funds = &env.message.sent_funds[0];
    if funds.denom != FUNDING_DENOM || funds.amount < Uint128(FUNDING_AMOUNT) {
        return Err(StdError::generic_err(
            "insufficient_funds 100000 uscrt required",
        ));
    }

state:
arr of win-table
init = payout adress,

msg:
roll() check if it can affor to payout get funds, roll. payout funds.  in frontend check  if there is in arr[] that funds got added
terminate() init can kill to release all funds in it

quary:
win-table.

todo: add entropy string to handle
# frontend
# anim:https://codesandbox.io/s/pyvo8mn5x0
# https://medium.com/@victortoschi/how-to-create-a-slot-machine-animation-with-css-and-javascript-9073ab9db9ea
objects got set postion with height calc ""boxesClone.style.transform = `translateY(-${door.clientHeight * (pool.length - 1)}px)`;""
then moved to 0

creat array of SlotTile component and calculate total height of arr
use x.start on anim