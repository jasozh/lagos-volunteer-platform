<script lang="ts">
  import Button from "$lib/components/atoms/Button.svelte";
  import ArrowOutwardIcon from "$lib/icons/ArrowOutwardIcon.svelte";
  import MobilePhoneIcon from "$lib/icons/MobilePhoneIcon.svelte";
  import DesktopIcon from "$lib/icons/DesktopIcon.svelte";
  import ButtonGroup from "$lib/components/molecules/ButtonGroup.svelte";
  import PlayIcon from "$lib/icons/PlayIcon.svelte";
  import GitHubIcon from "$lib/icons/GitHubIcon.svelte";
  import Carousel from "$lib/components/molecules/Carousel.svelte";
</script>

<div
  class="mx-auto flex min-h-screen max-w-screen-xl flex-col px-6 pb-12 pt-52"
>
  <div class="mx-auto text-5xl leading-tight">
    Volunteer management. <b class="text-[#568124]">Redefined.</b>
  </div>

  <div class="mx-auto my-12 flex w-full flex-col gap-3 md:w-fit md:flex-row">
    <Button size="xl">
      <div class="me-2"><PlayIcon /></div>
      Watch the video
    </Button>
    <Button size="xl">
      <div class="me-2"><ArrowOutwardIcon /></div>
      View the website
    </Button>
    <Button size="xl">
      <div class="me-2"><GitHubIcon /></div>
      See the code
    </Button>
  </div>

  <div class="mx-auto mb-3">
    <ButtonGroup>
      <Button size="icon" position="start">
        <MobilePhoneIcon size="sm" />
      </Button>
      <Button size="icon" position="end">
        <DesktopIcon size="sm" />
      </Button>
    </ButtonGroup>
  </div>

  <Carousel
    mode="fill"
    images={[
      {
        src: "https://flowbite.com/docs/images/carousel/carousel-1.svg",
        header: "View your events",
        label:
          "Easily see your entire event history by toggling between your upcoming and past events. Supervisors are also able to create/edit new events and manage all events created on the platform.",
      },
      {
        src: "https://flowbite.com/docs/images/carousel/carousel-2.svg",
        header: "Manage your attendees",
        label:
          "Say goodbye to cumbersome attendee tracking. See all attendees for a specific event and check them in and out with two clicks. You can also remove attendees from the registration list and keep track of attendees who canceled their registration.",
      },
      {
        src: "https://flowbite.com/docs/images/carousel/carousel-3.svg",
        header: "Manage your users",
        label:
          "Admins are able to see and manage every user on the platform. Check a volunteer’s event history to track their total number of volunteer hours, or blacklist them if they violate your rules and guidelines. You can also change user roles to add new supervisors and admins so you’re not managing all of your events alone.",
      },
      {
        src: "https://flowbite.com/docs/images/carousel/carousel-4.svg",
        header: "Register for events",
        label:
          "As a volunteer, you can register for events and keep track of your registration status. Can’t make an event? No worries! Cancel your registration and write a message to your supervisor letting them know.",
      },
      {
        src: "https://flowbite.com/docs/images/carousel/carousel-5.svg",
        header: "Track your hours",
        label:
          "See how your past events contribute to your volunteer history and how close you are to obtaining a reference or volunteer certificate. Once you reach the required number of hours, let your supervisor know. They can verify your event history directly from the platform.",
      },
    ]}
  />
</div>
