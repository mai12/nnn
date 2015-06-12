# 5.3 èٹ‚çڑ„ç»ƒن¹ 

### 5.3.1

ن¸‹é‌¢وک¯و¶‰هڈٹè؟گç®—ç¬¦ + ه’Œو•´و•°وˆ–وµ®ç‚¹è؟گç®—هˆ†é‡ڈçڑ„è،¨è¾¾ه¼ڈçڑ„و–‡و³•م€‚هŒ؛هˆ†وµ®ç‚¹و•°çڑ„و–¹و³•وک¯çœ‹ه®ƒوœ‰و— ه°ڈو•°ç‚¹م€‚

    E -> E + T | T
    T -> num.num | num
    
1. ç»™ه‡؛ن¸€ن¸ھ SDD و‌¥ç،®ه®ڑو¯ڈن¸ھé،¹ T ه’Œè،¨è¾¾ه¼ڈ E çڑ„ç±»ه‍‹
2. و‰©ه±•è؟™ن¸ھه¾—هˆ°çڑ„ SDDï¼Œن½؟ه¾—ه®ƒهڈ¯ن»¥وٹٹè،¨è¾¾ه¼ڈè½¬وچ¢وˆگن¸؛هگژç¼€è،¨è¾¾ه¼ڈم€‚ن½؟ç”¨ن¸€ن¸ھهچ•ç›®è؟گç®—ç¬¦ intToFloat وٹٹن¸€ن¸ھو•´و•°è½¬وچ¢ن¸؛ç›¸ç­‰çڑ„وµ®ç‚¹و•°م€‚

#### è§£ç­”

1. 

    <table>
        <thead>
            <tr>
                <th></th>
                <th>ن؛§ç”ںه¼ڈ</th>
                <th>è¯­و³•è§„هˆ™</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1)</td>
                <td>E -> E_1 + T</td>
                <td>E.type = E_1.type === float || T.type === float ? float : int</td>
            </tr>
            <tr>
                <td>2)</td>
                <td>E -> T</td>
                <td>E.type = T.type</td>
            </tr>
            <tr>
                <td>3)</td>
                <td>T -> num.num</td>
                <td>T.type = float</td>
            </tr>
            <tr>
                <td>4)</td>
                <td>T -> num</td>
                <td>T.type = int</td>
            </tr>
        </tbody>
    </table>


### 5.3.2 !

ç»™ه‡؛ن¸€ن¸ھ SDDï¼Œه°†ن¸€ن¸ھه¸¦وœ‰ + ه’Œ * çڑ„ن¸­ç¼€è،¨è¾¾ه¼ڈç؟»è¯‘وˆگو²،وœ‰ه†—ن½™و‹¬هڈ·çڑ„è،¨è¾¾ه¼ڈم€‚و¯”ه¦‚ه› ن¸؛ن¸¤ن¸ھè؟گç®—ç¬¦éƒ½وک¯ه·¦ç»“هگˆçڑ„ï¼Œه¹¶ن¸” * çڑ„ن¼که…ˆç؛§é«کن؛ژ +ï¼Œو‰€ن»¥ ((a\*(b+c))\*(d)) هڈ¯ç؟»è¯‘ن¸؛ a\*(b+c)\*d

#### è§£ç­”

ه‡ ن¸ھه±‍و€§è®¾ç½®ï¼ڑ

- wrapped: è،¨è¾¾ه¼ڈوœ€ه¤–ه±‚وک¯هگ¦وœ‰و‹¬هڈ·م€‚
- precedence: ن»¤ +ï¼Œ\*ï¼Œ() ه’Œهچ• digit çڑ„ن¼که…ˆç؛§هˆ†هˆ«ن¸؛ 0ï¼Œ1ï¼Œ2ï¼Œ3م€‚ ه¦‚و‍œè،¨è¾¾ه¼ڈوœ€ه¤–ه±‚وœ‰و‹¬هڈ·ï¼Œهˆ™ن¸؛هژ»وژ‰و‹¬هڈ·هگژوœ€هگژè¢«è®،ç®—çڑ„è؟گç®—ç¬¦çڑ„ن¼که…ˆç؛§ï¼Œهگ¦هˆ™ن¸؛è،¨è¾¾ه¼ڈوœ€هگژè¢«è®،ç®—çڑ„è؟گç®—ç¬¦çڑ„ن¼که…ˆç؛§م€‚
- expr: è،¨è¾¾ه¼ڈم€‚
- cleanExpr: هژ»é™¤ن؛†ه†—ن½™و‹¬هڈ·çڑ„è،¨è¾¾ه¼ڈم€‚

<table>
    <thead>
        <tr>
            <th></th>
            <th>ن؛§ç”ںه¼ڈ</th>
            <th>è¯­و³•è§„هˆ™</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1)</td>
            <td>L -> En</td>
            <td>
                L.cleanExpr = E.wrapped ? E.cleanExpr : E.expr
            </td>
        </tr>
        <tr>
            <td>2)</td>
            <td>E -> E_1 + T</td>
            <td>
                E.wrapped = false<br/>
                E.precedence = 0<br/>
                E.expr = E_1.expr || "+" || T.expr<br/>
                E.cleanExpr = (E_1.wrapped ? E_1.cleanExpr : E_1.expr) || "+" || (T.wrapped ? T.cleanExpr : T.expr)
            </td>
        </tr>
        <tr>
            <td>3)</td>
            <td>E -> T</td>
            <td>
                E.wrapped = T.wrapped<br/>
                E.precedence = T.precedence<br/>
                E.expr = T.expr</br>
                E.cleanExpr = T.cleanExpr
            </td>
        </tr>
        <tr>
            <td>4)</td>
            <td>T -> T_1 * F</td>
            <td>
                T.wrapped = false<br/>
                T.precedence = 1<br/>
                T.expr = T_1.expr || "*" || F.expr<br/>
                T.cleanExpr = (T_1.wrapped && T_1.precedence >= 1 ? T_1.cleanExpr : T_1) || * || (F.wrapped && F.precedence >= 1 ? F.cleanExpr : F.expr)
            </td>
        </tr>
        <tr>
            <td>5)</td>
            <td>T -> F</td>
            <td>
                T.wrapped = F.wrapped<br/>
                T.precedence = F.precedence<br/>
                T.expr = F.expr<br/>
                T.cleanExpr = F.cleanExpr
            </td>
        </tr>
        <tr>
            <td>6)</td>
            <td>F -> (E)</td>
            <td>
                F.wrapped = true<br/>
                F.precedence = E.precedence<br/>
                F.expr = "(" || E.expr || ")"<br/>
                F.cleanExpr = E.expr
            </td>
        </tr>
        <tr>
            <td>7)</td>
            <td>F -> digit</td>
            <td>
                F.wrapped = false<br/>
                F.precedence = 3<br/>
                F.expr = digit<br/>
                F.cleanExpr = digit
            </td>
        </tr>
    </tbody>
</table>

 
### 5.3.3 !

ç»™ه‡؛ن¸€ن¸ھ SDD ه¯¹ x\*(3\*x+x\*x) è؟™و ·çڑ„è،¨è¾¾ه¼ڈو±‚ه¾®هˆ†م€‚è،¨è¾¾ه¼ڈن¸­و¶‰هڈٹè؟گç®—ç¬¦ + ه’Œ * م€پهڈکé‡ڈ x ه’Œه¸¸é‡ڈم€‚هپ‡è®¾ن¸چè؟›è،Œن»»ن½•ç®€هŒ–ï¼Œن¹ںه°±وک¯è¯´ï¼Œو¯”ه¦‚ 3\*x ه°†è¢«ç؟»è¯‘ن¸؛ 3\*1+0\*xم€‚
