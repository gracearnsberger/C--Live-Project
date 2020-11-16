## C# Live Project Summary
  -In a two-week project, I collaborated with my peers in order to develop a wide scale web application built using ASP .Net MVC, Entity Framework, and C#, HTML, CSS, & razor syntax. I started this live project when it was in the middle of its lifecycle, so I was given the opportunity to help add features, debug, and refactor. With daily scrum meetings, I was able to get experience with a real life software engineering project simulation by gaining experience of peer collaboration, project management, version control, branch merging, and framework. The overall goal of this project is to use the web application as a content management service for a theater company in order to easily manage what content is displayed on their site and create different account access management under different logins on the site such as (admin, subscriber, and member).
 
   -Below you will be able to view my assigned stories, code snippets, as well as code files.  

* ### Change Layout of the Donor List Page & Add Modal:
 > I styled, organized, and exchanged data that displays on the donor list page of the website. I was able to use model, view, and controller pages to rearrange & change the information showing on the current page, edit some of it, and then display it all in a modal which will be called upon using a "details" button.

![Donor List View ](https://lh3.googleusercontent.com/-hpMJXJ5FLG4/X7LoIrCa5II/AAAAAAAAIVA/QvW9D8T3AiU2h9eOGENakTe1-RtW6qi6ACLcBGAsYHQ/s512/DonorListResult%2528webpage%2529png.png)![Donor List Modal View](https://lh3.googleusercontent.com/-czUwC8_wAEE/X7Lods3KI6I/AAAAAAAAIVY/bw4AFDEyVAcuU5tpfHEKOcpn0RG0cjzvACK8BGAsYHg/s512/DonorListModalResult%2528webpage%2529.png)


      <!--Button for Modal-->
      <div class="donorDetails">
        <button class="iconBtn" data-toggle="modal" data-target="#detailsModal" href="#sitecss" aria-expanded="false" aria-controls="sitecss">
          <i class="fa fa-info-circle fa-fw"></i>Details
        </button>
      </div>
    </div>

    <!--Display First Name, Last Name, and User Name on the Admin/Donorlist index page-->
    <table class="table admin-donorlist-table">
      <tr>
        <th>
          @Html.DisplayNameFor(model => model.SubscriberPerson.FirstName)
        </th>
        <th>
          @Html.DisplayNameFor(model => model.SubscriberPerson.LastName)
        </th>
        <th>
          @Html.DisplayNameFor(model => model.SubscriberPerson.UserName)
        </th>
        <th></th>
      </tr>

      @foreach (var item in Model)
      {
        <tr>
          <td>
            @Html.DisplayFor(modelItem => item.SubscriberPerson.FirstName)
          </td>
          <td>
            @Html.DisplayFor(modelItem => item.SubscriberPerson.LastName)
          </td>
          <td>
            @Html.DisplayFor(modelItem => item.SubscriberPerson.UserName)
          </td>
          <td>

            <!--Edit button for specific subscriber-->
            <button class="iconBtn donorButtons" data-toggle="collapse" onclick="location.href='@Url.Action("subscriber/Edit", "Subscribers", new { id = item.SubscriberId })'">
              <i class="fa fa-edit fa-fw"></i>@Html.ActionLink("Edit", "../Subscribers/subscriber/Edit", new { id = item.SubscriberId, Style = "color:White" }, null)
            </button>

            <!--Delete button for specific subscriber-->
            <button class="iconBtn donorButtons" data-toggle="collapse" onclick="location.href='@Url.Action("subscriber/Delete", "Subscribers", new { id = item.SubscriberId })'">
              <i class="fa fa-trash-alt fa-fw"></i>@Html.ActionLink("Delete", "../Subscribers/subscriber/Delete", new { id = item.SubscriberId })
            </button>
          </td>
        </tr>
      }
    </table>


    <!--Modal will display the subscribers name, subscribed (y/n)?, renewed (y/n)?, newsletter (y/n)?, recent-donor (y/n?), last-donation (date), donation amt($), special requests (y/n?), notes (y/n?)-->
    <!--Set modal sizing-->
    <div class="donor-modal-container">
      <div class="modal fade bs-example-modal-xl custom-modal" id="detailsModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-xl donor-modal" role="document">
          <div class="modal-content donor-content">
            <div class="modal-header">
              <!--Modal Title-->
              <h5 class="modal-title donor-modal-title" id="exampleModalLabel">Donor Details</h5>
              <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
              </button>
            </div>
            <div class="modal-body">
              <div class="donor-data">
                <!--Data and Titles displayed in Modal-->
                <table>
                  <tr>
                    <th></th>
                    <th>
                      Name &nbsp;
                    </th>
                    <th>
                      Subscribed? &nbsp;
                    </th>
                    <th>
                      Renewed? &nbsp;
                    </th>
                    <th>
                      Newsletter &nbsp;
                    </th>
                    <th>
                      Recent-Donor? &nbsp;
                    </th>
                    <th>
                      Last-Donation &nbsp;
                    </th>
                    <th>
                      Donation &nbsp;
                    </th>
                    <th>
                      Requests? &nbsp;
                    </th>
                    <th>
                      Notes &nbsp;
                    </th>
                  </tr>

                  @foreach (var item in Model)
                  {
                    <tr>
                      <th></th>
                      <td>
                        @Html.DisplayFor(modelItem => item.SubscriberPerson.FirstName)
                      </td>
                      <td>
                        @Html.DisplayFor(modelItem => item.CurrentSubscriber)
                      </td>
                      <td>
                        @Html.DisplayFor(modelItem => item.HasRenewed)
                      </td>
                      <td>
                        @Html.DisplayFor(modelItem => item.Newsletter)
                      </td>
                      <td>
                        @Html.DisplayFor(modelItem => item.RecentDonor)
                      </td>
                      <td>
                        @Html.DisplayFor(modelItem => item.LastDonated)
                      </td>
                      <td>
                        @Html.DisplayFor(modelItem => item.LastDonationAmt)
                      </td>
                      <td>
                        @Html.DisplayFor(modelItem => item.SpecialRequests)
                      </td>
                      <td>
                        @Html.DisplayFor(modelItem => item.Notes)
                      </td>
                    </tr>
                  }
                </table>
          


* ### Change Layout of the Change Password Page:
 > I added features and changed the layout of the Change Password page following the project styling and display the form. This form can only be accessed if the user is signed in under a subscribers account. This allows for security and content management on the site which was achieved using 
 > (html, c# (razor syntax), and css)

![Change Password Code Snippet](https://scontent.xx.fbcdn.net/v/t1.15752-0/p280x280/125553175_735660883692444_3978615744433834040_n.png?_nc_cat=105&ccb=2&_nc_sid=ae9488&_nc_ohc=o0pTxK42Or4AX96sBrG&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=d96552c04f88386e43302d10c6c2947d&oe=5FD67148)

<!--Create basic layout for Change Password page-->
<!--This page can only be accessed as a subscriber, admin, or donor-->
@using (Html.BeginForm("ChangePassword", "Manage", FormMethod.Post, new { @class = "form-horizontal", role = "form" }))
{
  <div class="card-passwordchange-container" style="width: 22rem;">
    <h2 class="change-password-title">@ViewBag.Title</h2>
    <!--Set sizing and labels for change password fields-->
    <div class="card-passwordchange-body">
      @Html.AntiForgeryToken()
      <hr />
      @Html.ValidationSummary("", new { @class = "text-danger" })
      <div class="form-group">
        @Html.LabelFor(m => m.OldPassword, new { @class = "form-text-labels" })
        <div class="col-md-12">
          @Html.PasswordFor(m => m.OldPassword, new { @class = "form-control" })
        </div>
      </div>
      <div class="form-group">
        @Html.LabelFor(m => m.NewPassword, new { @class = "form-text-labels" })
        <div class="col-md-12">
          @Html.PasswordFor(m => m.NewPassword, new { @class = "form-control" })
        </div>
      </div>
      <div class="form-group">
        @Html.LabelFor(m => m.ConfirmPassword, new { @class = "form-text-labels" })
        <div class="col-md-12">
          @Html.PasswordFor(m => m.ConfirmPassword, new { @class = "form-control" })
        </div>
      </div>
      <div class="form-group">
        <!--Submit Button for Change Password Field-->
        <div class="change-password-submit col-md-8">
          <input type="submit" value="Change password" class="btn btn-main" />
        </div>
      </div>
    </div>
  </div>


