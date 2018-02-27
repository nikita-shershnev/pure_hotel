<template>
  <div class="home">
    <header-content></header-content>

    <main>
      <div class="banner">
        <div class="banner__content">
          <svg viewBox="0 0 220 80" preserveAspectRatio="xMidYMid meet">
            <text x="110" y="77">A well-being oasis</text>
          </svg>
          <p>Hotel - Food & Drinks - Wellness - Music</p>
          <div class="mouse"></div>
          <div class="newsletter-wrapper">
            <button class="icon-button">
              <i class="material-icons ">mail_outline</i>
              <span class="outside-text">Newsletter</span>
            </button>
          </div>
        </div>
      </div>

      <section-content
        class="articles-section"
        title="EXCELLENCE AND QUALITY"
        subtitle="OASIS URBANO"
      >
        <div class="articles">
          <article-content title="Lorem ipsum dolor sit amet">
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quae sed, ut earum tempora, qui facilis voluptatem similique soluta magni, pariatur officiis molestiae distinctio tenetur praesentium ab porro. Commodi, tempore quasi.</p>
          </article-content>

          <article-content title="Lorem, ipsum">
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo excepturi et adipisci temporibus accusantium odio quidem cumque libero reprehenderit cum optio autem quasi corrupti odit eveniet, doloribus voluptas omnis expedita ducimus fugit ullam voluptatibus sint enim accusamus! Quod sit obcaecati sed!</p>
          </article-content>
        </div>
        <link-button>know more</link-button>
      </section-content>

      <divider></divider>

      <section-content
        class="articles-section"
        title="#PUROEXPERIENCE"
        subtitle="FEATURED EVENTS & EXPERIENCES"
      >
        <carousel :slides="slides"></carousel>
      </section-content>
    </main>

    <divider></divider>

    <footer-content></footer-content>
  </div>
</template>

<script>
import ArticleContent from '@/components/ArticleContent';
import Carousel from '@/components/Carousel';
import Divider from '@/components/Divider';
import FooterContent from '@/components/FooterContent';
import HeaderContent from '@/components/HeaderContent';
import LinkButton from '@/components/LinkButton';
import SectionContent from '@/components/SectionContent';

export default {
  name: 'home-container',

  data() {
    const slides = [
      {
        title: 'Title 1',
        subtitle: 'Subtitle 1',
        cost: '13',
      },
      {
        title: 'Title 2',
        subtitle: 'Subtitle 2',
      },
      {
        title: 'Title 3',
        subtitle: 'Subtitle 3',
        cost: '58',
      },
      {
        title: 'Title 4',
        subtitle: 'Subtitle 4',
        cost: '54',
      },
      {
        title: 'Title 5',
        subtitle: 'Subtitle 5',
        cost: '77',
      },
      {
        title: 'Title 6',
        subtitle: 'Subtitle 6',
        cost: '99',
      },
    ];
    return { slides };
  },

  components: {
    ArticleContent,
    Carousel,
    Divider,
    FooterContent,
    HeaderContent,
    LinkButton,
    SectionContent,
  },
};
</script>

<style lang="scss">
.banner {
  min-height: 100vh;
  position: relative;

  display: flex;
  align-items: flex-end;
  box-sizing: border-box;
  justify-content: center;

  padding-bottom: 30px;

  background: {
    image: url('../assets/img/banner.jpg');
    size: cover;
    position: center;
    attachment: fixed;
    repeat: no-repeat;
  }

  &__content {
    display: flex;
    flex-direction: column;
    align-items: center;

    text-align: center;
    width: 100%;
    max-width: 500px;
  }

  h2 {
    margin: 0;

    font-size: 1.5em;
  }

  p {
    margin: 6px 0 24px 0;

    font-size: 0.7em;
  }

  h2,
  p {
    text-transform: uppercase;
    color: #fff;
  }

  svg {
    width: 100%;
    height: 100%;

    text-anchor: middle;

    text {
      font-size: .7em;
      text-transform: uppercase;
      fill: #fff;
    }
  }

  .mouse {
    display: none;

    position: relative;

    width: 28px;
    height: 38px;

    box-sizing: border-box;

    opacity: 0.7;

    border: {
      width: 2px;
      style: solid;
      color: #fff;
      radius: 15px;
    }

    &:before {
      content: '';

      position: absolute;
      top: 20%;
      right: calc(50% - 3px);

      width: 6px;
      height: 6px;
      background-color: #fff;
      border-radius: 50%;

      animation: {
        name: mouse;
        duration: 1.2s;
        iteration-count: infinite;
      }
    }
  }

  .icon-button {
    width: 28px;
    height: 28px;
    box-sizing: border-box;

    position: relative;

    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;

    color: #fff;

    opacity: 0.7;

    cursor: pointer;

    border: {
      radius: 50%;
      width: 2px;
      color: #fff;
      style: solid;
    }

    i {
      font-size: 0.75em;
      margin-left: 1px;
    }

    &:focus,
    &:hover {
      .outside-text {
        right: 250%;
        opacity: 1;
      }
    }

    .outside-text {
      display: none;

      position: absolute;
      right: 200%;

      opacity: 0;

      font-size: 0.75em;
      text-transform: uppercase;

      transition: all .3s ease-in-out;

      &:after {
        content: '—';

        position: relative;
        left: 8px;
      }
    }
  }

  @media screen and (min-width: 900px) {
    .mouse {
      display: block;
    }

    .newsletter-wrapper {
      position: absolute;

      bottom: 30px;
      right: 30px;
    }

    .icon-button {
      .outside-text {
        display: block;
      }
    }

    i {
      margin-left: 0;
    }
  }
}

.articles {
  display: flex;
  flex-direction: column;
  margin-bottom: 24px;
}

@media screen and (min-width: 460px) {
  .articles {
    flex-direction: row;

    .article {
      &:not(:last-child) {
        margin-right: 24px;
      }
    }
  }
}

@media screen and (min-width: 460px) and (max-width: 900px) {
  .articles {
    flex-wrap: wrap;

    .article {
      width: 100%;
    }
  }
}

@media screen and (min-width: 1200px) {
  .articles-section {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;

    & > div:first-child {
      width: calc(40% - 24px);
      margin-right: 24px;
    }

    .articles {
      width: 60%;
    }
  }
}

.button:hover {
  .tooltip {
    display: block;
  }
}
</style>