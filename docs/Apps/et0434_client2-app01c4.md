# Client2 App01c4  (434)
## _Login Forms using Server JWT Auth API

<!-- <img src="Apps/images/et0434-04_client2-app01c4-register.mp4" class="img4"><br>-->
</br>

<video loop muted autoplay playsinline controls>
  <source src="Apps/images/et0434-04_client2-app01c4-register.mp4" />
  Please use a modern browser like Firefox or Chrome to see this helpful video.
</video>

</br></br>

## Notes:
This example will use the same Formik as the last example.  It also posts login data back to the server APIs, /api/auth/login and /api/auth/register with JWT tokens.

et0434-04_client2-app01c4-register.mp4

et0303-01_Install-MySQL.mp4

</br></br>

## Code:
```
import React from "react";

import { useHistory } from "react-router-dom";
import AuthService from "../services/auth.service";

function ProfilePage() {
  let history = useHistory();

  const currentUser = AuthService.getCurrentUser();

  if (!currentUser) {
    history.push("/home");
    window.location.reload();
  }

  return (
    <div>
      <br></br>
      <h4>User: {currentUser.username}</h4>
      <p>id: {currentUser.id}</p>
      <p>Email: {currentUser.email}</p>
      <p>Active: {currentUser.active}</p>
      <p>Role: {currentUser.role}</p>
      <p>PasswordDate: {currentUser.passworddate}</p>
      <p>
        Token:{" "}
        {currentUser.accessToken.substr(currentUser.accessToken.length - 20)}
      </p>
    </div>
  );
}

export default ProfilePage;

```
</br></br>

## Files:
```

|    Size     | Date Time       |./P08/Master/client2/app01c4/  *
| ----------  |---------------  |--------------------------------------------------------------------------
|           0 |2021-03-01 04:13 |./!_Login Forms using Server JWT Auth API
|         673 |2021-02-23 17:26 |./package.json
|        3439 |2021-02-23 17:26 |./README.md
|          52 |2021-02-23 17:53 |./.env
|             |                 |
|           0 |2021-02-26 10:21 |./public
|         281 |2021-02-26 10:21 |./public/index.html
|          70 |2021-02-23 17:26 |./public/robots.txt
|             |                 |
|           0 |2021-02-26 14:43 |./src
|        1695 |2021-03-01 03:54 |./src/App.js
|         390 |2021-02-24 08:54 |./src/index.js
|             |                 |
|           0 |2021-03-01 03:36 |./src/components
|         908 |2021-02-26 10:21 |./src/components/FormikControl.js
|        1706 |2021-02-26 14:43 |./src/components/LoginForm.js
|         203 |2021-02-26 14:43 |./src/components/Logout.js
|         598 |2021-02-26 14:43 |./src/components/NavBarNone.js
|         808 |2021-02-26 14:43 |./src/components/ProfilePage.js
|        2457 |2021-03-01 03:36 |./src/components/RegisterForm.js
|             |                 |
|           0 |2021-02-26 10:21 |./src/components/controls
|        1127 |2021-02-24 19:22 |./src/components/controls/Button.js
|        1045 |2021-02-26 10:21 |./src/components/controls/CheckboxGroup.js
|         894 |2021-02-26 10:21 |./src/components/controls/DatePicker.js
|         411 |2021-02-26 10:21 |./src/components/controls/Input copy.js
|         411 |2021-02-26 10:21 |./src/components/controls/Input.js
|         614 |2021-02-26 10:21 |./src/components/controls/Input3.js
|        1034 |2021-02-26 10:21 |./src/components/controls/RadioButtons.js
|         669 |2021-02-26 10:21 |./src/components/controls/Select.js
|         456 |2021-02-26 10:21 |./src/components/controls/Textarea.js
|         128 |2021-02-26 10:21 |./src/components/controls/TextError.js
|             |                 |
|           0 |2021-02-26 14:43 |./src/services
|         275 |2021-02-26 14:43 |./src/services/authHeader.js
|        1025 |2021-03-01 03:39 |./src/services/AuthService.js
|        5226 |2021-02-23 19:57 |./src/serviceWorker.js
|             |                 |

```
